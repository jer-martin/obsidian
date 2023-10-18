## Gradient Descent
- Gradient descent is a generic optimization algo
	- It is capable of finding optimal solutions to a wide range of problems
	- The general idea is to tweak iteratively in order to minimize a cost function

**REMEMBER THE FOGGY MOUNTAIN ANALOGY**

- Gradient Descent measures the local gradient of the error function with regard to the parameter vector $\theta$ 
	- Goes in direction of descending gradient (obviously)
	- Once grad is zero, we have reached a minimum

![center](../../zassets/Pasted%20image%2020231018165649.png)

*Learning Rate*
- This hyperparameter determines the size of the steps
	- Too small, it takes a long time
	- Too large and you jump across the valley, failing to diverge

**GRAD DESC REQUIRES FEATURE SCALING BECAUSE IT RELIES ON DISTANCE**

### Stochastic vs Batch
- Batch is more regular
	- Sits on the minima
![center](../../zassets/Pasted%20image%2020231018170241.png)

- Stochastic jumps around, can go positive again, but on average moves down the gradient
	- Doesn't settle on the minima
![center](Pasted%20image%2020231018170351.png)

