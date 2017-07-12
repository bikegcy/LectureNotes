TensorFlow Learning Note

### Get Started

Tensor:  A tensor consists of a set of primitive values shaped into an array of any number of dimensions.   

A tensor's rank is its number of dimensions. 

```python
3 # a rank 0 tensor; this is a scalar with shape []  
[1. ,2., 3.] # a rank 1 tensor; this is a vector with shape [3]  
[[1., 2., 3.], [4., 5., 6.]] # a rank 2 tensor; a matrix with shape [2, 3]
[[[1., 2., 3.]], [[7., 8., 9.]]] # a rank 3 tensor with shape [2, 1, 3]
```

TensorFlow Core programs:  

1. Building the computational graph  
2. Running the computational graph

A **computational graph** is a series of TensorFlow operations arranged into a graph of nodes. Each node takes an input(0 or more tensors) and outputs a tensor as an output.  

```python
node1 = tf.constant(3.0, dtype=tf.float32)
node2 = tf.constant(4.0) # also tf.float32 implicitly
print(node1, node2)
# tf.constant is one kind of node
# output: Tensor("Const:0", shape=(), dtype=float32) Tensor("Const_1:0", shape=(), dtype=float32)

# To evaluate the value, to run in sess
sess = tf.Session()
print(sess.run([node1, node2]))
# output: [3.0, 4.0]
```

