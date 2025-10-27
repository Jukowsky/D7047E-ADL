# Lab 3 Theory: Embedding Combination Methods

## Task 3.1.1 - Explain the pros and cons of utilising Concatenation for combining embeddings

Concatenation combines two embeddings by placing them side by side, resulting in a longer vector. This method is straightforward and preserves all the information from both inputs. However, it increases the overall dimensionality, which may lead to slower model training (more parameters) and a higher chance of overfitting. Additionally, concatenation does not capture interactions between the embeddings as it only stacks them.

## Task 3.1.2 - Explain the pros and cons of utilising Addition for combining embeddings

Addition combines embeddings by summing their corresponding elements. This keeps the combined representation compact and computationally efficient. It works well when both embeddings are aligned and share the same meaning. The downside is that it may lose important information, especially when the values in the embeddings cancel each other out. Moreover, it becomes difficult to trace which part of the output came from which input. Addition also requires embeddings to have the same size and scale, if image feature/word embedding have a larger magnitude than the other, the result may be skewed to one modality.

## Task 3.1.3 - Explain the pros and cons of utilising Multiplication for combining embeddings

Element-wise multiplication merges embeddings by multiplying corresponding values together. This allows the model to capture complex interactions between the features of each embedding and maintains the original embedding size. However, multiplication can also lead to loss of information if any values are zero or near-zero. It assumes that the embeddings are on a similar scale, which might not always be the case.

## Task 3.1.4 - Explain the pros and cons of utilising Attention for combining embeddings

Attention mechanisms combine embeddings by learning to assign different importance scores to each input. This helps the model focus on the most relevant parts of the data and better capture complex relationships. Attention also does not require embeddings to have the same dimensionality. While attention is very powerful, it is also more computationally intensive and requires more parameters and training data. It may also take longer to tune and get right compared to simpler methods.

## Task 3.1.5 - Explain the pros and cons of utilising Difference for combining embeddings

The difference method combines embeddings by subtracting one from the other. This is useful for tasks that involve comparison or contrast, such as similarity detection or question answering. It helps highlight what is unique or distinct between the two inputs. However, the resulting representation may amplify irrelevant differences or noise, and interpreting the resulting vector can be more challenging.
