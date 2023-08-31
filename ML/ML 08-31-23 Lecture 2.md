### Perceptron:
- Multiple inputs and weights combine into a weighted sum
- The weighted sum is compared to some constant to determine binary classification (yes or no)

```tikz
\begin{document}
  \begin{tikzpicture}[domain=0:4]
     \tikzstyle{unit}=[draw,shape=circle,minimum size=1.15cm]

\node[unit][fill={rgb,255:red,75;green,50;blue,150} ](p) at (2,1){$y$};
\node(dots) at (-0.25,1){\vdots};

\draw (0,2.5) node[xshift=-10]{$w_0$} -- (p);
\draw (0,1.75) node[xshift=-10]{$x_1$} --(p);
\draw (0,0) node[xshift=-10]{$x_D$} -- (p);
\draw (p) -- (3,1) node[xshift=30]{$y := f(z)$};
  \end{tikzpicture}
\end{document}
```
- Perceptrons can only solve problems that can be properly classified with a single line
### Multi-Layer Perceptron
- Multiple inputs, hidden layers

```tikz
\usepackage{tikz}
\begin{document}
\pagestyle{empty}

\def\layersep{2.5cm}

\begin{tikzpicture}[shorten >=1pt,->,draw=black!50, node distance=\layersep]
    \tikzstyle{every pin edge}=[<-,shorten <=1pt]
    \tikzstyle{neuron}=[circle,fill=black!25,minimum size=17pt,inner sep=0pt]
    \tikzstyle{input neuron}=[neuron, fill=green!50];
    \tikzstyle{output neuron}=[neuron, fill=red!50];
    \tikzstyle{hidden neuron}=[neuron, fill=blue!50];
    \tikzstyle{annot} = [text width=4em, text centered]

    % Draw the input layer nodes
    \foreach \name / \y in {1,...,4}
    % This is the same as writing \foreach \name / \y in {1/1,2/2,3/3,4/4}
        \node[input neuron, pin=left:Input \#\y] (I-\name) at (0,-\y) {};

    % Draw the hidden layer nodes
    \foreach \name / \y in {1,...,5}
        \path[yshift=0.5cm]
            node[hidden neuron] (H-\name) at (\layersep,-\y cm) {};

    % Draw the output layer node
    \node[output neuron,pin={[pin edge={->}]right:Output}, right of=H-3] (O) {};

    % Connect every node in the input layer with every node in the
    % hidden layer.
    \foreach \source in {1,...,4}
        \foreach \dest in {1,...,5}
            \path (I-\source) edge (H-\dest);

    % Connect every node in the hidden layer with the output layer
    \foreach \source in {1,...,5}
        \path (H-\source) edge (O);

    % Annotate the layers
    \node[annot,above of=H-1, node distance=1cm] (hl) {Hidden layer};
    \node[annot,left of=hl] {Input layer};
    \node[annot,right of=hl] {Output layer};
\end{tikzpicture}
% End of code
\end{document}
```

### K-Nearest Neighbors:
- Similar inputs have similar outputs
- For a test input, find k nearest neighbors in the training dataset and assign the most common label among them
- When considering more than one neighbor (k > 1), "voting" is used to assign a label
- Use an odd number k when there are only two classes
- Use weights = "distance": weight data points by the inverse of their distance
- If data is ordered by classes, you can add a slight amount of random noise to the data

- **How do we measure the distance?**
	- Euclidian: $d = (\sum\limits|x_{i}-z_{i}|^2)^{1/2}$ 
	- Manhattan: $d = \sum\limits|x_{i}-z_{i}|$
	- Minkowski: $d=(\sum\limits |x_{i}-z_{i}|^{p})^\frac{1}{p}$  


	Do we need to compute the distance to all training data points, or can we define a subset (i.e. neighbors) for which we compute the distance?

- **How do we find neighbors?**
	- Brute force
		- Computes distance to *every* point in the training set
		- Most accurate method as it considers every point
		- Each time you test a new point, you will have to recompute all distances
	- KD Tree
		- K-Dimensional Tree
		- Developed to reduce the required number of distance calculations
		- The node divisions of the KD Tree are axis-aligned and cannot take a different shape
		- Works well for low-dimensional data ($KD < 10$), but not as well for high-dimensional data
	- Ball Tree
		- Similar to KD Tree, but uses circles instead of lines
		- Works better in higher dimensions, slower in low dimensions ($KD < 3$)
- Tree Layout
```tikz
\begin{document}


\tikzset{every picture/.style={line width=0.75pt}} %set default line width to 0.75pt        

\begin{tikzpicture}[x=0.75pt,y=0.75pt,yscale=-1,xscale=1]
%uncomment if require: \path (0,300); %set diagram left start at 0, and has height of 300

%Shape: Rectangle [id:dp9089914825037735] 
\draw   (120,34) -- (190,34) -- (190,74) -- (120,74) -- cycle ;
%Shape: Rectangle [id:dp22316835426709547] 
\draw   (39,94) -- (109,94) -- (109,134) -- (39,134) -- cycle ;
%Shape: Rectangle [id:dp5779677343606187] 
\draw   (199,94) -- (269,94) -- (269,134) -- (199,134) -- cycle ;
%Shape: Rectangle [id:dp8966897151024569] 
\draw   (13,167) -- (83,167) -- (83,207) -- (13,207) -- cycle ;
%Shape: Rectangle [id:dp14409860471567337] 
\draw   (98,166) -- (168,166) -- (168,206) -- (98,206) -- cycle ;
%Shape: Rectangle [id:dp2667025851523892] 
\draw   (184,163) -- (254,163) -- (254,203) -- (184,203) -- cycle ;
%Shape: Rectangle [id:dp5658911937141065] 
\draw   (266,159) -- (336,159) -- (336,199) -- (266,199) -- cycle ;
%Straight Lines [id:da9858763191924067] 
\draw    (137.5,75) -- (84.4,92.38) ;
\draw [shift={(82.5,93)}, rotate = 341.88] [color={rgb, 255:red, 0; green, 0; blue, 0 }  ][line width=0.75]    (10.93,-3.29) .. controls (6.95,-1.4) and (3.31,-0.3) .. (0,0) .. controls (3.31,0.3) and (6.95,1.4) .. (10.93,3.29)   ;
%Straight Lines [id:da7380225042170054] 
\draw    (180.5,75) -- (216.69,92.14) ;
\draw [shift={(218.5,93)}, rotate = 205.35] [color={rgb, 255:red, 0; green, 0; blue, 0 }  ][line width=0.75]    (10.93,-3.29) .. controls (6.95,-1.4) and (3.31,-0.3) .. (0,0) .. controls (3.31,0.3) and (6.95,1.4) .. (10.93,3.29)   ;
%Straight Lines [id:da2737085325296942] 
\draw    (210.5,136) -- (213.29,162.01) ;
\draw [shift={(213.5,164)}, rotate = 263.88] [color={rgb, 255:red, 0; green, 0; blue, 0 }  ][line width=0.75]    (10.93,-3.29) .. controls (6.95,-1.4) and (3.31,-0.3) .. (0,0) .. controls (3.31,0.3) and (6.95,1.4) .. (10.93,3.29)   ;
%Straight Lines [id:da779489927238344] 
\draw    (233.5,136) -- (293.63,159.28) ;
\draw [shift={(295.5,160)}, rotate = 201.16] [color={rgb, 255:red, 0; green, 0; blue, 0 }  ][line width=0.75]    (10.93,-3.29) .. controls (6.95,-1.4) and (3.31,-0.3) .. (0,0) .. controls (3.31,0.3) and (6.95,1.4) .. (10.93,3.29)   ;
%Straight Lines [id:da47346243758721585] 
\draw    (99.5,137) -- (129.97,162.71) ;
\draw [shift={(131.5,164)}, rotate = 220.16] [color={rgb, 255:red, 0; green, 0; blue, 0 }  ][line width=0.75]    (10.93,-3.29) .. controls (6.95,-1.4) and (3.31,-0.3) .. (0,0) .. controls (3.31,0.3) and (6.95,1.4) .. (10.93,3.29)   ;
%Straight Lines [id:da47950393268158065] 
\draw    (47.5,135) -- (31.44,165.23) ;
\draw [shift={(30.5,167)}, rotate = 297.98] [color={rgb, 255:red, 0; green, 0; blue, 0 }  ][line width=0.75]    (10.93,-3.29) .. controls (6.95,-1.4) and (3.31,-0.3) .. (0,0) .. controls (3.31,0.3) and (6.95,1.4) .. (10.93,3.29)   ;




\end{tikzpicture}

\end{document}
```

- **Feature scaling (very important!)
	- Make sure there isn't a multiplier on either scale, will mess up neighbor finding algorithm
		- We need to "preprocess" the training set before we apply KNN
			- Standardization: $x_{st}=\frac{x-\bar{x}}{\sigma}$ 
			- Normalization: $x_{norm}=\frac{x-x_{min}}{x_{max}-x_{min}}$ 
	- We compute $\bar{x}, \sigma, x_{min}, x_{max}$ using the *training dataset only*, and then apply standardization/normalization to  ***both***  training and testing datasets


- **Curse of dimensionality**
	- There are $n$ data points randomly distributed in $D$-dimensional space
	- Lets find the $k$ nearest neighbors around a test point
	- Let $l$ be the edge length of the smallest hypercube that contains $k$ neighbors
	- Can you express $l$ using $n, D,$ and $k$?
		- Yes
		- $\frac{l^{D}}{1^{D}}\approx\frac{k}{n}$, so $l \approx (\frac{k}{n})^\frac{1}{D}$ 
	- 