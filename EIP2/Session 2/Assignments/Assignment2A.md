Math steps during learning(forward path) and back propagation (gradient descent).

$Step0:$

 Read the input and output

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
    <th colspan = 4>X</th>
    <th colspan = 3>wh</th> 
    <th colspan = 3>bh</th>
    <th colspan = 3>hidden_layer_input</th>
    <th colspan = 3>hidden_layer_activations</th>  
    <th>wout</th>
    <th>bout</th>
         <th>ouput</th>
    <th>y</th>
    <th>E</th>
    </tr>
<tr><td>1</td> <td>0</td> <td>1</td> <td>0</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td>1 </td> <td> </td>  </tr>
    <br>
<tr><td>1</td> <td>0</td> <td>1</td> <td>1</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td> 1</td> <td> </td>  </tr>
    <br>
<tr><td>0</td> <td>1</td> <td>0</td> <td>1</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td> 0</td> <td> </td>  </tr>
    <br>
    <tr><td></td> <td></td> <td></td> <td></td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td> </td>  </tr>
</table>





$Step1$: Initialize weights and biases with random values

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
    <th colspan = 4>             X</th>
    <th colspan = 3>           wh</th> 
    <th colspan = 3>           bh</th>
    <th colspan = 3>hidden_layer_input</th>
    <th colspan = 3>hidden_layer_activations</th>  
    <th>wout</th>
    <th>bout</th>
    <th>output</th>
    <th>y</th>
    <th>E</th>
    </tr>
<tr><td>1</td> <td>0</td> <td>1</td> <td>0</td> <td>0.22</td> <td>0.36</td> <td>0.77</td> 
    <td>0.38</td> <td>0.87</td> <td>0.12</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td></td> <td>0.22</td> <td>0.72</td><td> </td> <td>1</td> <td> </td> </tr>
    <br>
<tr><td>1</td> <td>0</td> <td>1</td> <td>1</td> <td>0.12</td> <td>0.67</td> <td>0.08</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td>0.35</td> <td></td><td> </td> <td>1</td> <td> </td>  </tr>
    <br>
<tr><td>0</td> <td>1</td> <td>0</td> <td>1</td> <td>0.60</td> <td>0.18</td> <td>0.34</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td>0.40</td> <td></td> <td> </td><td>0</td> <td> </td>   </tr>
   <br> 
 <tr><td></td> <td></td> <td></td> <td></td> <td>0.44</td> <td>0.90</td> <td>0.80</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td></td> <td> </td>   </tr>
</table>



$Step2$:

 Calculate hidden layer input:
`hidden_layer_input= matrix_dot_product(X,wh) + bh`

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
    <th colspan = 4>             X</th>
    <th colspan = 3>           wh</th> 
    <th colspan = 3>           bh</th>
    <th colspan = 3>hidden_layer_input</th>
    <th colspan = 3>hidden_layer_activations</th>  
    <th>wout</th>
    <th>bout</th>
         <th>output</th>
    <th>y</th>
    <th>E</th>
    </tr>
<tr><td>1</td> <td>0</td> <td>1</td> <td>0</td> <td>0.22</td> <td>0.36</td> <td>0.77</td> 
    <td>0.38</td> <td>0.87</td> <td>0.12</td> <td>1.20</td> <td>1.41</td> <td>1.23</td> 
    <td></td> <td> </td> <td> </td> <td>0.22</td> <td>0.72</td> <td></td> <td>1 </td> <td> </td>  </tr>
    <br>
<tr><td>1</td> <td>0</td> <td>1</td> <td>1</td> <td>0.12</td> <td>0.67</td> <td>0.08</td> <td></td> <td></td> <td></td> <td>1.64</td> <td>2.31</td> <td>2.03</td> <td> </td> <td> </td> <td> </td> <td>0.35</td><td></td><td></td> <td> 1</td> <td> </td>  </tr>
    <br>
<tr><td>0</td> <td>1</td> <td>0</td> <td>1</td> <td>0.60</td> <td>0.18</td> <td>0.34</td> <td> </td> <td> </td> <td> </td> <td>0.94</td> <td>2.44</td> <td>1.00</td> <td> </td> <td> </td> <td> </td> <td>0.40</td> <td> </td><td></td> <td> 0</td> <td> </td>  </tr>
    <br>
 <tr><td></td> <td></td> <td></td> <td></td> <td>0.44</td> <td>0.90</td> <td>0.80</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> <td></td></td> <td> </td>  </tr>
</table>



$Step  3:$Perform non-linear transformation on hidden linear input

`hiddenlayer_activations = sigmoid(hidden_layer_input)`

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
    <th colspan = 4>             X</th>
    <th colspan = 3>           wh</th> 
    <th colspan = 3>           bh</th>
    <th colspan = 3>hidden_layer_input</th>
    <th colspan = 3>hidden_layer_activations</th>  
    <th>wout</th>
    <th>bout</th>
    <th>output</th>     
    <th>y</th>
    <th>E</th>
    </tr>
<tr><td>1</td> <td>0</td> <td>1</td> <td>0</td> <td>0.22</td> <td>0.36</td> <td>0.77</td> 
    <td>0.38</td> <td>0.87</td> <td>0.12</td> <td>1.20</td> <td>1.41</td> <td>1.23</td> 
    <td>0.77</td> <td>0.80</td> <td>0.77</td> <td>0.22</td> <td>0.72</td><td></td> <td>1 </td> <td> </td>  </tr>
    <br>
<tr><td>1</td> <td>0</td> <td>1</td> <td>1</td> <td>0.12</td> <td>0.67</td> <td>0.08</td> <td></td> <td></td> <td></td> <td>1.64</td> <td>2.31</td> <td>2.03</td> <td>0.84</td>
    <td>0.91</td> <td>0.88</td> <td>0.35</td> <td> </td> <td></td><td>1</td> <td> </td>  </tr>
    <br>
<tr><td>0</td> <td>1</td> <td>0</td> <td>1</td> <td>0.60</td> <td>0.18</td> <td>0.34</td> <td> </td> <td> </td> <td> </td> <td>0.94</td> <td>2.44</td> <td>1.00</td> <td>0.72</td> <td>0.92</td> <td>0.73</td> <td>0.40</td> <td></td><td> </td> <td> 0</td> <td> </td>  </tr>
    <br>
 <tr><td></td> <td></td> <td></td> <td></td> <td>0.44</td> <td>0.90</td> <td>0.80</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td> </td> <td> </td>  </tr>
</table>



$Step4$:  Perform linear and non-linear transformation of hidden layer activation at output layer

`output_layer_input = matrix_dot_product (hiddenlayer_activations * wout ) + bout`
 `output = sigmoid(output_layer_input)`

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
    <th colspan = 4>             X</th>
    <th colspan = 3>           wh</th> 
    <th colspan = 3>           bh</th>
    <th colspan = 3>hidden_layer_input</th>
    <th colspan = 3>hidden_layer_activations</th>  
    <th>wout</th>
    <th>bout</th>
    <th>output</th>     
    <th>y</th>
    <th>E</th>
    </tr>
<tr><td>1</td> <td>0</td> <td>1</td> <td>0</td> <td>0.22</td> <td>0.36</td> <td>0.77</td> 
    <td>0.38</td> <td>0.87</td> <td>0.12</td> <td>1.20</td> <td>1.41</td> <td>1.23</td> 
    <td>0.77</td> <td>0.80</td> <td>0.77</td> <td>0.22</td> <td>0.72</td><td>0.81</td> <td>1 </td> <td> </td>  </tr>
    <br>
<tr><td>1</td> <td>0</td> <td>1</td> <td>1</td> <td>0.12</td> <td>0.67</td> <td>0.08</td> <td></td> <td></td> <td></td> <td>1.64</td> <td>2.31</td> <td>2.03</td> <td>0.84</td>
    <td>0.91</td> <td>0.88</td> <td>0.35</td> <td> </td> <td>0.83</td><td>1</td> <td> </td>  </tr>
    <br>
<tr><td>0</td> <td>1</td> <td>0</td> <td>1</td> <td>0.60</td> <td>0.18</td> <td>0.34</td> <td> </td> <td> </td> <td> </td> <td>0.94</td> <td>2.44</td> <td>1.00</td> <td>0.72</td> <td>0.92</td> <td>0.73</td> <td>0.40</td> <td></td><td>0.82</td> <td>0</td> <td> </td>  </tr>
    <br>
 <tr><td></td> <td></td> <td></td> <td></td> <td>0.44</td> <td>0.90</td> <td>0.80</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td> </td> <td> </td>  </tr>
</table>

$Step5:$Calculate gradient of Error(E) at output layer
`E = y-output`

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
    <th colspan = 4>             X</th>
    <th colspan = 3>           wh</th> 
    <th colspan = 3>           bh</th>
    <th colspan = 3>hidden_layer_input</th>
    <th colspan = 3>hidden_layer_activations</th>  
    <th>wout</th>
    <th>bout</th>
    <th>output</th>     
    <th>y</th>
    <th>E</th>
    </tr>
<tr><td>1</td> <td>0</td> <td>1</td> <td>0</td> <td>0.22</td> <td>0.36</td> <td>0.77</td> 
    <td>0.38</td> <td>0.87</td> <td>0.12</td> <td>1.20</td> <td>1.41</td> <td>1.23</td> 
    <td>0.77</td> <td>0.80</td> <td>0.77</td> <td>0.22</td> <td>0.72</td><td>0.81</td> <td>1 </td> <td>0.19</td>  </tr>
    <br>
<tr><td>1</td> <td>0</td> <td>1</td> <td>1</td> <td>0.12</td> <td>0.67</td> <td>0.08</td> <td></td> <td></td> <td></td> <td>1.64</td> <td>2.31</td> <td>2.03</td> <td>0.84</td>
    <td>0.91</td> <td>0.88</td> <td>0.35</td> <td> </td> <td>0.83</td><td>1</td> <td>0.17 </td>  </tr>
    <br>
<tr><td>0</td> <td>1</td> <td>0</td> <td>1</td> <td>0.60</td> <td>0.18</td> <td>0.34</td> <td> </td> <td> </td> <td> </td> <td>0.94</td> <td>2.44</td> <td>1.00</td> <td>0.72</td> <td>0.92</td> <td>0.73</td> <td>0.40</td> <td></td><td>0.82</td> <td>0</td> <td>-0.82</td>  </tr>
    <br>
 <tr><td></td> <td></td> <td></td> <td></td> <td>0.44</td> <td>0.90</td> <td>0.80</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td> </td> <td> </td>  </tr>
</table>



$Step6:$  Compute slope at output and hidden layer
`Slope_output_layer= derivatives_sigmoid(output)`
`Slope_hidden_layer = derivatives_sigmoid(hiddenlayer_activations)`

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
    <th colspan = 4>             X</th>
    <th colspan = 3>           wh</th> 
    <th colspan = 3>           bh</th>
    <th colspan = 3>hidden_layer_input</th>
    <th colspan = 3>hidden_layer_activations</th>  
    <th>wout</th>
    <th>bout</th>
    <th>output</th>     
    <th>y</th>
    <th>E</th>
    </tr>
<tr><td>1</td> <td>0</td> <td>1</td> <td>0</td> <td>0.22</td> <td>0.36</td> <td>0.77</td> 
    <td>0.38</td> <td>0.87</td> <td>0.12</td> <td>1.20</td> <td>1.41</td> <td>1.23</td> 
    <td>0.77</td> <td>0.80</td> <td>0.77</td> <td>0.22</td> <td>0.72</td><td>0.81</td> <td>1 </td> <td>0.19</td>  </tr>
    <br>
<tr><td>1</td> <td>0</td> <td>1</td> <td>1</td> <td>0.12</td> <td>0.67</td> <td>0.08</td> <td></td> <td></td> <td></td> <td>1.64</td> <td>2.31</td> <td>2.03</td> <td>0.84</td>
    <td>0.91</td> <td>0.88</td> <td>0.35</td> <td> </td> <td>0.83</td><td>1</td> <td>0.17 </td>  </tr>
    <br>
<tr><td>0</td> <td>1</td> <td>0</td> <td>1</td> <td>0.60</td> <td>0.18</td> <td>0.34</td> <td> </td> <td> </td> <td> </td> <td>0.94</td> <td>2.44</td> <td>1.00</td> <td>0.72</td> <td>0.92</td> <td>0.73</td> <td>0.40</td> <td></td><td>0.82</td> <td>0</td> <td>-0.82</td>  </tr>
    <br>
 <tr><td></td> <td></td> <td></td> <td></td> <td>0.44</td> <td>0.90</td> <td>0.80</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td> </td> <td> </td>  </tr>
</table>



<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
         <th colspan = 3>									Slope_hidden_layer </th>
    </tr>
    <tr>
        <td>0.18</td><td>0.16</td> <td>0.18</td>
    </tr>
    <tr>
        <td>0.14</td> <td>0.08</td> <td>0.10</td>
    </tr>
    <tr>
        <td>0.20</td> <td>0.07</td> <td>0.20</td>
    </tr>
</table>

| Slope Output |
| ------------ |
| 0.15         |
| 0.14         |
| 0.15         |



$Step 7:$  Compute delta at output layer

`d_output = E \* slope_output_layer*lr`

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
    <th colspan = 4>             X</th>
    <th colspan = 3>           wh</th> 
    <th colspan = 3>           bh</th>
    <th colspan = 3>hidden_layer_input</th>
    <th colspan = 3>hidden_layer_activations</th>  
    <th>wout</th>
    <th>bout</th>
    <th>output</th>     
    <th>y</th>
    <th>E</th>
    </tr>
<tr><td>1</td> <td>0</td> <td>1</td> <td>0</td> <td>0.22</td> <td>0.36</td> <td>0.77</td> 
    <td>0.38</td> <td>0.87</td> <td>0.12</td> <td>1.20</td> <td>1.41</td> <td>1.23</td> 
    <td>0.77</td> <td>0.80</td> <td>0.77</td> <td>0.22</td> <td>0.72</td><td>0.81</td> <td>1 </td> <td>0.19</td>  </tr>
    <br>
<tr><td>1</td> <td>0</td> <td>1</td> <td>1</td> <td>0.12</td> <td>0.67</td> <td>0.08</td> <td></td> <td></td> <td></td> <td>1.64</td> <td>2.31</td> <td>2.03</td> <td>0.84</td>
    <td>0.91</td> <td>0.88</td> <td>0.35</td> <td> </td> <td>0.83</td><td>1</td> <td>0.17 </td>  </tr>
    <br>
<tr><td>0</td> <td>1</td> <td>0</td> <td>1</td> <td>0.60</td> <td>0.18</td> <td>0.34</td> <td> </td> <td> </td> <td> </td> <td>0.94</td> <td>2.44</td> <td>1.00</td> <td>0.72</td> <td>0.92</td> <td>0.73</td> <td>0.40</td> <td></td><td>0.82</td> <td>0</td> <td>-0.82</td>  </tr>
    <br>
 <tr><td></td> <td></td> <td></td> <td></td> <td>0.44</td> <td>0.90</td> <td>0.80</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td> </td> <td> </td>  </tr>
</table>

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
         <th colspan = 3>									Slope_hidden_layer </th>
    </tr>
    <tr>
        <td>0.18</td><td>0.16</td> <td>0.18</td>
    </tr>
    <tr>
        <td>0.14</td> <td>0.08</td> <td>0.10</td>
    </tr>
    <tr>
        <td>0.20</td> <td>0.07</td> <td>0.20</td>
    </tr>
</table>

| Slope Output | E     |
| ------------ | ----- |
| 0.15         | 0.19  |
| 0.14         | 0.17  |
| 0.15         | -0.82 |

| Delta Output |
| ------------ |
| 0.03         |
| 0.02         |
| -0.12        |

$Step 8:$ Calculate Error at hidden layer

`Error_at_hidden_layer = matrix_dot_product(d_output, wout.Transpose)`

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
    <th colspan = 4>             X</th>
    <th colspan = 3>           wh</th> 
    <th colspan = 3>           bh</th>
    <th colspan = 3>hidden_layer_input</th>
    <th colspan = 3>hidden_layer_activations</th>  
    <th>wout</th>
    <th>bout</th>
    <th>output</th>     
    <th>y</th>
    <th>E</th>
    </tr>
<tr><td>1</td> <td>0</td> <td>1</td> <td>0</td> <td>0.22</td> <td>0.36</td> <td>0.77</td> 
    <td>0.38</td> <td>0.87</td> <td>0.12</td> <td>1.20</td> <td>1.41</td> <td>1.23</td> 
    <td>0.77</td> <td>0.80</td> <td>0.77</td> <td>0.22</td> <td>0.72</td><td>0.81</td> <td>1 </td> <td>0.19</td>  </tr>
    <br>
<tr><td>1</td> <td>0</td> <td>1</td> <td>1</td> <td>0.12</td> <td>0.67</td> <td>0.08</td> <td></td> <td></td> <td></td> <td>1.64</td> <td>2.31</td> <td>2.03</td> <td>0.84</td>
    <td>0.91</td> <td>0.88</td> <td>0.35</td> <td> </td> <td>0.83</td><td>1</td> <td>0.17 </td>  </tr>
    <br>
<tr><td>0</td> <td>1</td> <td>0</td> <td>1</td> <td>0.60</td> <td>0.18</td> <td>0.34</td> <td> </td> <td> </td> <td> </td> <td>0.94</td> <td>2.44</td> <td>1.00</td> <td>0.72</td> <td>0.92</td> <td>0.73</td> <td>0.40</td> <td></td><td>0.82</td> <td>0</td> <td>-0.82</td>  </tr>
    <br>
 <tr><td></td> <td></td> <td></td> <td></td> <td>0.44</td> <td>0.90</td> <td>0.80</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td> </td> <td> </td>  </tr>
</table>



| Slope Output | E     |
| ------------ | ----- |
| 0.15         | 0.19  |
| 0.14         | 0.17  |
| 0.15         | -0.82 |

| Delta Output |
| ------------ |
| 0.03         |
| 0.02         |
| -0.12        |

   <head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
         <th colspan = 3>			Slope_hidden_layer </th>
         <th colspan = 3>			Error_at_hidden_layer </th>
    </tr>
    <tr>
        <td>0.18</td><td>0.16</td> <td>0.18</td> <td>0.007</td><td>0.011</td> <td>0.012</td>
    </tr>
    <tr>
        <td>0.14</td> <td>0.08</td> <td>0.10</td> <td>0.004</td> <td>0.007</td> <td>0.008</td>
    </tr>
    <tr>
        <td>0.20</td> <td>0.07</td> <td>0.20</td><td>-0.026</td> <td>-0.042</td> <td>-0.048</td>
    </tr>
    </table>

 $Step9:$ Compute delta at hidden layer

`d_hiddenlayer = Error_at_hidden_layer \* slope_hidden_layer`

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
    <th colspan = 4>             X</th>
    <th colspan = 3>           wh</th> 
    <th colspan = 3>           bh</th>
    <th colspan = 3>hidden_layer_input</th>
    <th colspan = 3>hidden_layer_activations</th>  
    <th>wout</th>
    <th>bout</th>
    <th>output</th>     
    <th>y</th>
    <th>E</th>
    </tr>
<tr><td>1</td> <td>0</td> <td>1</td> <td>0</td> <td>0.22</td> <td>0.36</td> <td>0.77</td> 
    <td>0.38</td> <td>0.87</td> <td>0.12</td> <td>1.20</td> <td>1.41</td> <td>1.23</td> 
    <td>0.77</td> <td>0.80</td> <td>0.77</td> <td>0.22</td> <td>0.72</td><td>0.81</td> <td>1 </td> <td>0.19</td>  </tr>
    <br>
<tr><td>1</td> <td>0</td> <td>1</td> <td>1</td> <td>0.12</td> <td>0.67</td> <td>0.08</td> <td></td> <td></td> <td></td> <td>1.64</td> <td>2.31</td> <td>2.03</td> <td>0.84</td>
    <td>0.91</td> <td>0.88</td> <td>0.35</td> <td> </td> <td>0.83</td><td>1</td> <td>0.17 </td>  </tr>
    <br>
<tr><td>0</td> <td>1</td> <td>0</td> <td>1</td> <td>0.60</td> <td>0.18</td> <td>0.34</td> <td> </td> <td> </td> <td> </td> <td>0.94</td> <td>2.44</td> <td>1.00</td> <td>0.72</td> <td>0.92</td> <td>0.73</td> <td>0.40</td> <td></td><td>0.82</td> <td>0</td> <td>-0.82</td>  </tr>
    <br>
 <tr><td></td> <td></td> <td></td> <td></td> <td>0.44</td> <td>0.90</td> <td>0.80</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td> </td> <td> </td>  </tr>
</table>

| Slope Output | E     |
| ------------ | ----- |
| 0.15         | 0.19  |
| 0.14         | 0.17  |
| 0.15         | -0.82 |

| Delta Output |
| ------------ |
| 0.03         |
| 0.02         |
| -0.12        |

   <head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
         <th colspan = 3>			Slope_hidden_layer </th>
         <th colspan = 3>			Error_at_hidden_layer </th>
    </tr>
    <tr>
        <td>0.18</td><td>0.16</td> <td>0.18</td> <td>0.007</td><td>0.011</td> <td>0.012</td>
    </tr>
    <tr>
        <td>0.14</td> <td>0.08</td> <td>0.10</td> <td>0.004</td> <td>0.007</td> <td>0.008</td>
    </tr>
    <tr>
        <td>0.20</td> <td>0.07</td> <td>0.20</td><td>-0.026</td> <td>-0.042</td> <td>-0.048</td>
    </tr>
    </table>    

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
         <th colspan = 3>									Delta_hidden_layer </th>
    </tr>
    <tr>
        <td>-0.003</td><td>-0.004</td> <td>-0.005</td>
    </tr>
    <tr>
        <td>-0.001</td> <td>-0.002</td> <td>-0.002</td>
    </tr>
    <tr>
        <td>-0.003</td> <td>-0.005</td> <td>-0.006</td>
    </tr>
</table>

$Step10:$ Update weight at both output and hidden layer

```
wout = wout + matrix_dot_product(hiddenlayer_activations.Transpose, d_output) * learning_rate
```

```
 wh =  wh+ matrix_dot_product(X.Transpose,d_hiddenlayer) * learning_rate
```

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
    <th colspan = 4>             X</th>
    <th colspan = 3>           wh</th> 
    <th colspan = 3>           bh</th>
    <th colspan = 3>hidden_layer_input</th>
    <th colspan = 3>hidden_layer_activations</th>  
    <th>wout</th>
    <th>bout</th>
    <th>output</th>     
    <th>y</th>
    <th>E</th>
    </tr>
<tr><td>1</td> <td>0</td> <td>1</td> <td>0</td> <td>0.22</td> <td>0.36</td> <td>0.77</td> 
    <td>0.38</td> <td>0.87</td> <td>0.12</td> <td>1.20</td> <td>1.41</td> <td>1.23</td> 
    <td>0.77</td> <td>0.80</td> <td>0.77</td> <td>0.215</td> <td>0.72</td><td>0.81</td> <td>1 </td> <td>0.19</td>  </tr>
    <br>
<tr><td>1</td> <td>0</td> <td>1</td> <td>1</td> <td>0.12</td> <td>0.67</td> <td>0.08</td> <td></td> <td></td> <td></td> <td>1.64</td> <td>2.31</td> <td>2.03</td> <td>0.84</td>
    <td>0.91</td> <td>0.88</td> <td>0.344</td> <td> </td> <td>0.83</td><td>1</td> <td>0.17 </td>  </tr>
    <br>
<tr><td>0</td> <td>1</td> <td>0</td> <td>1</td> <td>0.60</td> <td>0.18</td> <td>0.34</td> <td> </td> <td> </td> <td> </td> <td>0.94</td> <td>2.44</td> <td>1.00</td> <td>0.72</td> <td>0.92</td> <td>0.73</td> <td>0.395</td> <td></td><td>0.82</td> <td>0</td> <td>-0.82</td>  </tr>
    <br>
 <tr><td></td> <td></td> <td></td> <td></td> <td>0.44</td> <td>0.90</td> <td>0.80</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td> </td> <td> </td>  </tr>
</table>

| Slope Output | E     |
| ------------ | ----- |
| 0.15         | 0.19  |
| 0.14         | 0.17  |
| 0.15         | -0.82 |

| Delta Output |
| ------------ |
| 0.03         |
| 0.02         |
| -0.12        |

   <head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
         <th colspan = 3>			Slope_hidden_layer </th>
         <th colspan = 3>			Error_at_hidden_layer </th>
    </tr>
    <tr>
        <td>0.18</td><td>0.16</td> <td>0.18</td> <td>0.007</td><td>0.011</td> <td>0.012</td>
    </tr>
    <tr>
        <td>0.14</td> <td>0.08</td> <td>0.10</td> <td>0.004</td> <td>0.007</td> <td>0.008</td>
    </tr>
    <tr>
        <td>0.20</td> <td>0.07</td> <td>0.20</td><td>-0.026</td> <td>-0.042</td> <td>-0.048</td>
    </tr>
    </table>    

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
         <th colspan = 3>									Delta_hidden_layer </th>
    </tr>
    <tr>
        <td>-0.003</td><td>-0.004</td> <td>-0.005</td>
    </tr>
    <tr>
        <td>-0.001</td> <td>-0.002</td> <td>-0.002</td>
    </tr>
    <tr>
        <td>-0.003</td> <td>-0.005</td> <td>-0.006</td>
    </tr>
</table>

`learning rate =0.1 `

wh matrix remains almost same as the value of ` matrix_dot_product(X.Transpose,d_hiddenlayer)*learning_rate` is of order $10^{-4} $



$Step11:$ Update biases at both output and hidden layer

`bh = bh + sum(d_hiddenlayer, axis=0) \* learning_rate`

`bout = bout + sum(d_output, axis=0)\*learning_rate`

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
    <th colspan = 4>             X</th>
    <th colspan = 3>           wh</th> 
    <th colspan = 3>           bh</th>
    <th colspan = 3>hidden_layer_input</th>
    <th colspan = 3>hidden_layer_activations</th>  
    <th>wout</th>
    <th>bout</th>
    <th>output</th>     
    <th>y</th>
    <th>E</th>
    </tr>
<tr><td>1</td> <td>0</td> <td>1</td> <td>0</td> <td>0.22</td> <td>0.36</td> <td>0.77</td> 
    <td>0.38</td> <td>0.87</td> <td>0.12</td> <td>1.20</td> <td>1.41</td> <td>1.23</td> 
    <td>0.77</td> <td>0.80</td> <td>0.77</td> <td>0.215</td> <td>0.72</td><td>0.81</td> <td>1 </td> <td>0.19</td>  </tr>
    <br>
<tr><td>1</td> <td>0</td> <td>1</td> <td>1</td> <td>0.12</td> <td>0.67</td> <td>0.08</td> <td></td> <td></td> <td></td> <td>1.64</td> <td>2.31</td> <td>2.03</td> <td>0.84</td>
    <td>0.91</td> <td>0.88</td> <td>0.344</td> <td> </td> <td>0.83</td><td>1</td> <td>0.17 </td>  </tr>
    <br>
<tr><td>0</td> <td>1</td> <td>0</td> <td>1</td> <td>0.60</td> <td>0.18</td> <td>0.34</td> <td> </td> <td> </td> <td> </td> <td>0.94</td> <td>2.44</td> <td>1.00</td> <td>0.72</td> <td>0.92</td> <td>0.73</td> <td>0.395</td> <td></td><td>0.82</td> <td>0</td> <td>-0.82</td>  </tr>
    <br>
 <tr><td></td> <td></td> <td></td> <td></td> <td>0.44</td> <td>0.90</td> <td>0.80</td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td> <td> </td><td> </td> <td> </td> <td> </td>  </tr>
</table>

​        

| Slope Output | E     |
| ------------ | ----- |
| 0.15         | 0.19  |
| 0.14         | 0.17  |
| 0.15         | -0.82 |

| Delta Output |
| ------------ |
| 0.03         |
| 0.02         |
| -0.12        |

   <head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
         <th colspan = 3>			Slope_hidden_layer </th>
         <th colspan = 3>			Error_at_hidden_layer </th>
    </tr>
    <tr>
        <td>0.18</td><td>0.16</td> <td>0.18</td> <td>0.007</td><td>0.011</td> <td>0.012</td>
    </tr>
    <tr>
        <td>0.14</td> <td>0.08</td> <td>0.10</td> <td>0.004</td> <td>0.007</td> <td>0.008</td>
    </tr>
    <tr>
        <td>0.20</td> <td>0.07</td> <td>0.20</td><td>-0.026</td> <td>-0.042</td> <td>-0.048</td>
    </tr>
    </table>    

<head>
<style>
table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
}
</style>
</head>
<table >
     <tr>
         <th colspan = 3>									Delta_hidden_layer </th>
    </tr>
    <tr>
        <td>-0.003</td><td>-0.004</td> <td>-0.005</td>
    </tr>
    <tr>
        <td>-0.001</td> <td>-0.002</td> <td>-0.002</td>
    </tr>
    <tr>
        <td>-0.003</td> <td>-0.005</td> <td>-0.006</td>
    </tr>
</table>

Again bh is almost same because  `sum(d_hiddenlayer, axis=0) * learning_rate` approximates to $10^{-4}$ This is also the case of bout