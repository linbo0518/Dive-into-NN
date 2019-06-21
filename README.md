# Dive into NN: Theory, Architecture and Initialization

Oral for AI-ML-Club(`AMC` for short), for more detail about our club, check out our [GitHub](https://github.com/BUPT/ai-ml.club) and [Website](https://ai-ml.club/)

- [Dive into NN: Theory, Architecture and Initialization](#Dive-into-NN-Theory-Architecture-and-Initialization)
  - [Material](#Material)
    - [Paper](#Paper)
    - [Link](#Link)
  - [Slide](#Slide)
  - [Thinking](#Thinking)

## Material

### Paper

- [Rethinking The Value of Network Pruning](https://arxiv.org/abs/1810.05270)
- [The Lottery Ticket Hypothesis- Finding Sparse, Trainable Neural Networks](https://arxiv.org/abs/1803.03635)
- [The Benefits of Over-parameterization at Initialization in Deep ReLU Networks](https://arxiv.org/abs/1901.03611)
- [Stabilizing the Lottery Ticket Hypothesis](https://arxiv.org/abs/1903.01611)
- [Luck Matters: Understanding Training Dynamics of Deep ReLU Networks](https://arxiv.org/abs/1905.13405)
- [How to Initialize your Network](https://arxiv.org/abs/1906.02341)

### Link

- [如何评价ICLR 2019最佳论文《The Lottery Ticket Hypothesis》？](https://www.zhihu.com/question/323214798)
- [求道之人，不问寒暑（三）](https://zhuanlan.zhihu.com/p/67782029)

## Slide

[Google Slide](https://docs.google.com/presentation/d/1cQqC3SRYlZypvQFtG7pvkBzYK1hMgu8HjwO5qvlX48Q/edit?usp=sharing)(under construction...)

## Thinking

- [x] Rethinking The Value of Network Pruning

Paper

> 1. training a large, over-parameterized model is often not necessary to obtain an efficient final model
> 2. learned “important” weights of the large model are typically not useful for the small pruned model
> 3. the pruned architecture itself, rather than a set of inherited “important” weights, is more crucial to the efficiency in the final model, which suggests that in some cases pruning can be useful as an architecture search paradigm.

Zhihu

> 这里再总结一下paper关于LTH的实验（也包括LTH原paper的实验），就是：在unstructured pruning上，当使用小的learning rate时，winning ticket有帮助；当使用（标准的且accuracy更高的）大learning rate时，winning ticket没有帮助；在L1-norm structured pruning上，不管大小learning rate, winning ticket都没有帮助。更多讨论见我们paper的section 6。这个回答并没有想说LTH的价值不大，只是想指出可能有些其他情况它并不成立。至于为什么即使对unstructured pruning, 也只有当小learning rate的时候LTH才成立，我的一个naive的猜想是（并没有经过实验验证，轻喷），当learning rate较小时，最终训完时候的weights和original initialization时候的weights距离较小（不一定是L2 distance,可能是更抽象的），所以如果使用original initialization来对小model进行初始化，相当于leak了一些training完后的大model的信息。极端一点的话，甚至可以说，使用了winning ticket的这个小model并不是从scratch训的，而是已经某种程度上based on这个已经train了很久的大model了，所以它能train的相对好。当使用大learning rate时，训完的weights和init的相差较远，就不存在这个原因了。

- [x] The Lottery Ticket Hypothesis- Finding Sparse, Trainable Neural Networks

Paper

> 1. **The Lottery Ticket Hypothesis**. A randomly-initialized, dense neural network contains a subnetwork that is initialized such that—when trained in isolation—it can match the test accuracy of the original network after training for at most the same number of iterations.
> 2. The lottery ticket hypothesis offers a complementary perspective on this relationship—that larger networks might explicitly contain simpler representations.
> 3. By this logic, overparameterized networks are easier to train because they have more combinations of subnetworks that are potential winning tickets.

Zhihu

> 就是说初始参数固定了，最优子网络就固定了。


- [ ] The Benefits of Over-parameterization at Initialization in Deep ReLU Networks
- [ ] Stabilizing the Lottery Ticket Hypothesis
- [ ] Luck Matters: Understanding Training Dynamics of Deep ReLU Networks
- [ ] How to Initialize your Network
