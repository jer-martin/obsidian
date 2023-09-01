To do List:
1. review mod1 class website
2. read the celestial sphere list of terms
3. print star wheel on card stock paper

## Four Fundamental Propositions of Greek Astronomy
### 1. The Earth is a sphere
- What observations can you make to determine the shape of the Earth?
	- Aristotle noticed the Earth's shadow is curved during a lunar eclipse
	- Travelers reported that height of the Pole star above horizon varies as you travel North to South
### 2. The Earth doesn't move
- Why would they think that the Earth doesn't move?
	- We do not feel the Earth moving
	- Objects thrown upward drop back to point of departure
	- If Earth moved about the Sun, then we should observe ***stellar parallax***
### 3. The heavens move spherically
- Why spherical?
	- Star trails
### 4. The Earth sits at the center of the heavens
- Everything seemed to move around the Earth

## Motion of the Sun
- #### Annual Motion
	- caused by Earth's orbit around the Sun
- #### Ecliptic
	- path of the Sun in the sky
	- inclined 23.5$\textdegree$ relative to the [[NEWTN 09-01-23 Lecture 4|Celestial Equator]]

```tikz


\begin{document}      

\begin{tikzpicture}[x=0.75pt,y=0.75pt,yscale=-1,xscale=1]
%uncomment if require: \path (0,300); %set diagram left start at 0, and has height of 300

%Shape: Circle [id:dp9420091796824002] 
\draw   (2,87.25) .. controls (2,41.82) and (38.82,5) .. (84.25,5) .. controls (129.68,5) and (166.5,41.82) .. (166.5,87.25) .. controls (166.5,132.68) and (129.68,169.5) .. (84.25,169.5) .. controls (38.82,169.5) and (2,132.68) .. (2,87.25) -- cycle ;
%Straight Lines [id:da0841313899417444] 
\draw    (84.25,5) -- (84.25,169.5) ;
%Straight Lines [id:da6801576982665467] 
\draw    (2,87.25) -- (166.5,87.25) ;
%Shape: Circle [id:dp05860915502419739] 
\draw  [fill={rgb, 255:red, 74; green, 144; blue, 226 }  ,fill opacity=1 ] (106,87.25) .. controls (106,78.28) and (113.28,71) .. (122.25,71) .. controls (131.22,71) and (138.5,78.28) .. (138.5,87.25) .. controls (138.5,96.22) and (131.22,103.5) .. (122.25,103.5) .. controls (113.28,103.5) and (106,96.22) .. (106,87.25) -- cycle ;
%Straight Lines [id:da12163161009756807] 
\draw    (143.5,27) -- (143.5,142) (147.5,37) -- (139.5,37)(147.5,47) -- (139.5,47)(147.5,57) -- (139.5,57)(147.5,67) -- (139.5,67)(147.5,77) -- (139.5,77)(147.5,87) -- (139.5,87)(147.5,97) -- (139.5,97)(147.5,107) -- (139.5,107)(147.5,117) -- (139.5,117)(147.5,127) -- (139.5,127)(147.5,137) -- (139.5,137) ;
%Shape: Circle [id:dp9375374692095124] 
\draw  [fill={rgb, 255:red, 248; green, 231; blue, 28 }  ,fill opacity=1 ] (133.5,92.25) .. controls (133.5,89.49) and (135.74,87.25) .. (138.5,87.25) .. controls (141.26,87.25) and (143.5,89.49) .. (143.5,92.25) .. controls (143.5,95.01) and (141.26,97.25) .. (138.5,97.25) .. controls (135.74,97.25) and (133.5,95.01) .. (133.5,92.25) -- cycle ;

% Text Node
\draw (160,135) node [anchor=north west][inner sep=0.75pt]   [align=left] {CE};


\end{tikzpicture}
\end{document}

```

**These observations led to the Celestial Sphere**!

### The Celestial Sphere
- Earth's North and South poles define the CS's poles
- the equator defines the CE
- stars and sun are attached to the sphere
- Earth rotates from W to E, therefore stars appear to rotate E to W

```tikz
\begin{document}
    \begin{tikzpicture}[
        dot/.style = {outer sep = 0, inner sep = 0, shape = circle, label = {#1}},
        dot/.default =,
        small dot/.style = {minimum size = .2cm, dot = {#1}},
        small dot/.default =,]
        % Equator
        \draw[thick] (-6,0) arc (180:360:6cm and 1cm);
        \draw[thick, dashed, opacity=.6] (-6,0) arc (180:0:6cm and 1cm);
        % Ecliptic of the sun (back)
        \draw[thick, dashed, rotate=23.5, color=blue, opacity=.6] (-6,0) arc (180:0:6cm and 1cm);
        % Celestial sphere
        \draw[thick] (0,0) circle (6cm);
        \shade[ball color=blue!10!white,opacity=0.20] (0,0) circle (6cm);
        % Earth
        \draw[thick] (0,0) circle (0.5cm);
        \shade[ball color=blue!60!white,opacity=0.80] (0,0) circle (0.5cm);
        % Sun
        \draw[thick] (5.5024,2.392) circle (0.5cm);
        \shade[ball color=yellow!60!white,opacity=0.8] (5.5024,2.392) circle (0.5cm);
        % Ecliptic of the sun (front)
        \draw[thick, rotate=23.5, color=blue] (-6,0) arc (180:360:6cm and 1cm);
        % Vernal equinox
        \node[fill = black, draw = black, small dot = {right: }] at (0.2,-1) {};
    \end{tikzpicture}
\end{document}
```
                                Blue is Ecliptic, White is Celestial Equator
### Equatorial Coordinates
- ##### Right Ascension
    - Longitude
- ##### Declination
    - Latitude
- Units
    - RA
        - hr, min, sec
        - 360 degrees / 24 hrs = 15 degrees / hr
    - Dec
        - degrees, arcmin, arcsec
```tikz
\usepackage{tikz}

\usetikzlibrary{bending}
\begin{document}
    \begin{tikzpicture}[
        dot/.style = {outer sep = 0, inner sep = 0, shape = circle, label = {#1}},
        dot/.default =,
        small dot/.style = {minimum size = .2cm, dot = {#1}},
        small dot/.default =,]
        % Equator
        \draw[thick] (-6,0) arc (180:360:6cm and 1cm);
        \draw[thick, dashed, opacity=.6] (-6,0) arc (180:0:6cm and 1cm);
        % Ecliptic of the sun (back)
        \draw[thick, dashed, rotate=23.5, color=blue, opacity=.6] (-6,0) arc (180:0:6cm and 1cm);
        % Celestial sphere
        \draw[thick] (0,0) circle (6cm);
        \shade[ball color=blue!10!white,opacity=0.20] (0,0) circle (6cm);
        % Earth
        \draw[thick] (0,0) circle (0.5cm);
        \shade[ball color=blue!60!white,opacity=0.80] (0,0) circle (0.5cm);
        % Sun
        \draw[thick] (5.5024,2.392) circle (0.5cm);
        \shade[ball color=yellow!60!white,opacity=0.8] (5.5024,2.392) circle (0.5cm);
        % Ecliptic of the sun (front)
        \draw[thick, rotate=23.5, color=blue] (-6,0) arc (180:360:6cm and 1cm);
        % Vernal equinox
        \node[fill = black, draw = black, small dot = {right: }] at (0.2,-1) {};

        % red is RA, green is Dec
        \draw[red, very thick, ->] (.2,-1) arc (-90:0:5.8 and 1.02);
        \draw[green, very thick, ->] ++(6cm,0) arc (0:23:6cm);
    \end{tikzpicture}
\end{document}
```
    
                                            Red is RA, green is Declination

- ##### Precession
    - causes changes in coordinates over time
