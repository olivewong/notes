## Other models

### Simplistic - autocorrect
- "I on the phone screen on the phone screen on the phone screen ..."
- Markov chains
- Just does based on the most recent, doesn't really look back, same with feedforward

### Recurrent neural networks
- Keeps a vector (its memory), modifies the vector with each word

### LSTMs
- Actively decide what to keep or forget

## Attention
- Decide which parts of the input to keep, and which to ignore
- The system learns what to pay attention to 
- Makes it more debuggable/interpretable because you can see what it's "paying attention" to 
-

## Transformer
- Neural network that relies heavily on attention
- Not recurrent
    - Output does not get fed back to input every time
    - When it wants to know something, it uses attention to go back
    - https://www.youtube.com/watch?v=S27pHKBEp30
