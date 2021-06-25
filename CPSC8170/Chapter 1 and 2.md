TARGET DECK: Main Deck

Define an analog signal (engineering) #fc 
An analog signal is a continuous signal that represents physical measurements.
<!--ID: 1623255160639-->


Define digital #fc 
Digital signals are time separated signals which are generated using digital modulation. It uses a continuous range of values that help you to represent information. Digital signal uses discrete 0 and 1 to represent information.
<!--ID: 1623255160679-->


Update step for $\mathbf x^{[n]}$ and $\mathbf v^{[n]}$ in euler integration with an acceleration $\mathbf a^{[n]}$ over a time step $h$. (using start of interval) #fc 
$$\mathbf v^{[n+1]} = \mathbf v^{[n]} + h \mathbf a^{[n]}$$ 
$$\mathbf x^{[n+1]} = \mathbf x^{[n]} + h \mathbf v^{[n]}$$ 
<!--ID: 1623255160681-->


Pseudocode for a simple falling ball animation. #fc 
```
v0 = 0, x0 = 100;
t = 0, n = 0;
while t < tmax:
	a_n = -10
	if t is an output frame time:
		output v, x
	v[n+1] = v[n] + h*a[n]
	x[n+1] = x[n] + h*v[n]
```
<!--ID: 1623255160684-->


Which integration approach will give you exact answers for a constant acceleration? What are the equations #fc 
Eurler integration taking the average values at the start and end of the interval ie.
```
v[n+1] = v[n] + a[n]*h
x[n+1] = x[n] + (v[n] + v[n+1])*h/2
```
<!--ID: 1623255160686-->


Simple model for accounting for the force due to air resistance (assume a constant $k$): what is the acceleration? #fc
$$ \mathbf F = \mathbf F_g + \mathbf F_a$$
$$m\mathbf a = m \mathbf g - k \mathbf v$$
$$\mathbf a = \mathbf g - \frac{k}{m} \mathbf v$$
<!--ID: 1623255160689-->

How is wind modelled (what is the acceleration due to gravity + air resistance + wind)? #fc 
$$\mathbf a = \mathbf g + \frac{k}{m}(\mathbf v_{wind} - \mathbf v)$$
Notice that $(\mathbf v_{wind} - \mathbf v)$ is the relative velocity of the object with respect to the air.
<!--ID: 1623255328314-->


