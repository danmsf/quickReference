
# TensorFlow Snippets

## Session Setup

## Variable Creation

## TensorBoard

## Functions

### General

* **tf.placeholder(tf.int32, [batch_size, seq_length])** = saves a place for values that havent been called or created yet

    *example:*
        input_data = tf.placeholder(tf.int32, [batch_size, seq_length])
        
        
* **tf.get_variable** = if variable doesnt exist it initializes it; otherwise it takes the existing version; 

    *example:*
        softmax_w = tf.get_variable("softmax_w", [dim0_size, dim1_size])
* **tf.squeeze** = removes dimensions of size 1 from the tensor
* **tf.matmul** = matrix multiply

### RNNs

* **cell.zero_state**  = will initialize the required state class; will return the state with all the values equal to 0.0.; it is agnostic of the type of the cell (LSTM, GRU, RNN) and you can do something like this:

        if type == 'GRU':
           cell = BasicGRUCell
        else:
           cell = BasicLSTMCell(state_is_tuple=True)

        init_state = cell.zero_state(batch_size)
* **cell.LSTMStateTuple** = when you're initializing your state with custom values (passed by the trainer).
ref (https://stackoverflow.com/questions/43192809/lstmstatetuple-vs-cell-zero-state-for-rnn-in-tensorflow)

## Random

* **protocol buffer** = a language agnostic method of serialization; googles is called `protoc`
(https://developers.google.com/protocol-buffers/)


```python
!jupyter nbconvert --to markdown TensorFlow.ipynb
```
