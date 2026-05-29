# GenAI Academy – Session 2: Slide Text & Speaker Notes

---

## Slide 1: Title – GenAI Academy Session 2

**Speaker Notes:**
Welcome everyone to Session 2 of the GenAI Academy. Today we're going to dive into the core technologies that make generative AI possible — starting with the fundamentals of neural networks, then moving into how machines see images through computer vision, and finally how they understand human language through natural language processing. These three pillars form the technical foundation that ultimately led to the large language models and AI agents we'll explore in later sessions. Very little mathemtics is included, apart from linear algebra concepts. By the end of today, you'll understand  how neural networks are used to classify images and start to imagine how they are used to embedd text. 

---

## Slide 2: Today's Agenda

**Speaker Notes:**
Let me outline what we'll cover today. First, we'll start with neural network fundamentals — understanding how a single neuron works, how networks learn through backpropagation, and what frameworks like TensorFlow and PyTorch provide. Then we'll move into computer vision, where convolutional neural networks revolutionized image understanding. Finally, we'll tackle natural language processing — how text gets transformed into numbers that neural networks can work with, from simple bag-of-words approaches all the way to transformers. These aren't isolated topics; they tell a coherent story of how AI evolved to handle increasingly complex tasks.

---

## Slide 3: Schedule

**Speaker Notes:**
Here's our schedule for today. Don't hesitate to ask questions at any point — these concepts build on each other. I hope I am able to answer them. 

---

## Slide 4: From 0/1 to Neural Networks - From last session 

**Speaker Notes:**
Last time - We started with zeros and ones — pure binary computation. Then came algorithms and rule-based expert systems where humans manually encoded knowledge. But rules break down for tasks like recognizing a cat in a photo — you can't write enough if-then statements for that. The breakthrough was making rules learnable: functions with adjustable parameters that improve from data. Neural networks excelled at this, finding patterns that humans couldn't manually program. Then came the massive scale-up — large language models with billions of parameters that can write poetry, generate code, and reason about abstract concepts. And now we have entered the era of AI agents — systems that don't just respond passively but actively pursue goals.

---

## Slide 5: Neural Networks (Section Header) - "Interconnected learning units" 

**Speaker Notes:**
Now we enter the core of today's session — neural networks. The concept is elegantly simple: take inputs, multiply them by learnable weights, sum them up, and apply a non-linear function. What makes them powerful is that by connecting many such simple units in layers and training them on data, they can approximate incredibly complex functions. Everything we'll discuss today — CNNs for vision, RNNs for language, transformers — they're all variations on this fundamental idea of interconnected learning units.

---

## Slide 6: Model of a Neuron

**Speaker Notes:**
Here's the fundamental building block of all neural networks — the artificial neuron. Just like a biological neuron has dendrites that receive signals and an axon that sends output, our mathematical model takes N inputs, each multiplied by a weight that represents the strength of that connection. The formula is simple: **Y equals f of the weighted sum of inputs** — where f is our activation function. **The weights are what the network learns during training.** The activation function introduces non-linearity, which is crucial — without it, stacking layers would be no better than a single layer, because linear functions composed together are still linear. Common activation functions include sigmoid, tanh, and the now-dominant ReLU.

---

## Slide 7: Introduction to Neural Networks: Perceptron

**Speaker Notes:**
The **perceptron** is where it all began. In 1957, Frank Rosenblatt built the Mark-1 perceptron at Cornell — a physical machine with a 20-by-20 photocell array and potentiometers for weights that could recognize basic shapes like triangles and squares. The New York Times predicted it would eventually walk, talk, and be conscious. To recap, the math is straightforward: **multiply inputs by weights, sum them, and if the result is positive, output plus-one; otherwise, output minus-one.** Training adjusts weights using gradient descent — when the perceptron makes a mistake, nudge the weights in the right direction. But here's the critical limitation: a single perceptron can only draw a straight-line decision boundary. It famously cannot solve XOR — and this limitation led to the "AI winter" until multi-layer networks and backpropagation solved the problem.

---

## Slide 8: Neural Network Frameworks - brief

**Speaker Notes:**
When building neural networks in practice, you don't implement backpropagation from scratch — you use frameworks. The two dominant ones are **TensorFlow, backed by Google**, and PyTorch, backed by Meta. Both solve the same two fundamental problems: first, they provide optimized tensor operations that can run on GPUs for massive parallelism; second, they handle automatic differentiation — computing all the gradients needed for backpropagation automatically. Each framework offers both low-level APIs for researchers building custom architectures and high-level APIs like Keras or PyTorch Lightning where you simply stack layers and call dot-fit. The high-level APIs handle training loops, batching, and optimization — letting you go from idea to trained model in just a few lines of code.

---

## Slide 9: Overfitting - good one 

**Speaker Notes:**
Overfitting is perhaps the most important practical challenge in machine learning. Imagine you have just five data points and you fit a polynomial with seven parameters — you'll pass through every point perfectly with zero training error, but the curve will be wildly wrong between the points. That's overfitting: your model has learned the noise, not the signal. You detect it by watching validation loss — when it starts rising while training loss keeps falling, you're overfitting. The key prevention strategies are: use more training data, reduce model complexity, or apply regularization like dropout, which randomly zeroes out neurons during training to prevent co-adaptation. This connects to the bias-variance tradeoff — too simple and you underfit, too complex and you overfit. The sweet spot is where validation performance peaks.

---

## Slide 10: LAB – MNIST Binary Classification - N/A 

**Speaker Notes:**
Now let's put theory into practice. The MNIST dataset contains 70,000 images of handwritten digits, each 28-by-28 pixels in grayscale. It's the "hello world" of machine learning — simple enough to train quickly, complex enough to demonstrate real learning. In this lab, we'll build a binary classifier that distinguishes between two digits. You'll see how raw pixel values become input features, how the network learns to identify the distinctive strokes of each digit, and how training loss decreases over epochs. Pay attention to the difference between training and validation accuracy — this is where you'll see overfitting in real time if the model trains too long. This exercise connects directly to the perceptron and multi-layer network concepts we just covered.

---

## Slide 11: Computer Vision (Section Header) - brief or skip 

**Speaker Notes:**
We're now moving into computer vision — teaching machines to see and understand images. While a simple fully-connected network can handle centered, uniform images like MNIST digits, real-world vision is far more challenging. Objects appear at different locations, scales, and orientations. The breakthrough came with convolutional neural networks (CNNs), which are specifically designed to handle spatial data by learning local patterns that can be detected anywhere in an image. CNNs build a hierarchy of features: early layers detect edges and textures, middle layers combine these into shapes and parts, and deep layers recognize complete objects. This mirrors how the human visual cortex processes information — from simple to complex.

---

## Slide 12: Well-Known CNN Architectures – VGG-16

**Speaker Notes:**
VGG-16 is one of the most influential CNN architectures because of its elegant simplicity. It consists of blocks of convolution layers followed by max-pooling, repeated five times, then three fully-connected layers at the end. **The "16" refers to its 16 weight layers.** What makes VGG-16 special is its clean, predictable structure — it proved that simply stacking more layers with small 3-by-3 filters could achieve remarkable accuracy. At 92.7 percent top-5 accuracy on ImageNet's thousand categories, it was state-of-the-art in 2014. Today, it's still widely used as a feature extractor for transfer learning — because it learned such general-purpose visual features, you can take its pre-trained convolutional layers and apply them to completely new image classification tasks with minimal additional training.

---

## Slide 13: ImageNet Classification Competition

**Speaker Notes:**
ImageNet is the competition that ignited the deep learning revolution. It contains millions of labeled images across a thousand categories — from dog breeds to vehicle types to household objects. Before 2012, the best approaches used hand-crafted features and achieved around 74 percent top-5 accuracy. Then Alex Krizhevsky's AlexNet, a deep CNN trained on GPUs, shattered all records by jumping to over 84 percent accuracy — a massive leap that proved deep learning worked at scale. After that, every winning entry was a CNN: VGG-16 in 2014, GoogLeNet with its Inception modules, and Microsoft's ResNet in 2015, which surpassed human-level performance using revolutionary skip connections. This competition single-handedly convinced the AI community that deep neural networks were the path forward.

---

## Slide 14: VIDEO – How a Convolutional Layer Works - N/A 

**Speaker Notes:**
This video illustrates the core mechanism of CNNs — the convolutional layer. Imagine a small window, say 3-by-3 pixels, sliding across the entire image one position at a time. At each position, it multiplies the pixel values by the filter weights and sums them up — producing one number that indicates how strongly that pattern is present at that location. A vertical edge filter, for example, will produce high values wherever there's a vertical edge in the image. The key innovation of CNNs is that these filters aren't hand-designed by engineers — they're learned automatically during training. The network discovers for itself that it needs edge detectors, texture detectors, and shape detectors, arranged in increasingly abstract layers. This is what makes CNNs so powerful: they find the optimal features for any visual task.

---

## Slide 15: Natural Language Processing (Section Header)

**Speaker Notes:**
We've covered how neural networks see images — now let's talk about how they understand language. NLP is in many ways more challenging than computer vision because language is inherently abstract, ambiguous, and contextual. The same word can mean completely different things depending on context — "bank" can be a financial institution or a river bank. The fundamental problem we need to solve is representation: how do you convert words, which are arbitrary symbols, into numbers that neural networks can process while preserving meaning? This question has driven decades of research, from simple word counting methods to the sophisticated embedding techniques that power today's language models. Let's trace that evolution.

---

## Slide 16: Representing Text As Vectors

**Speaker Notes:**
Here's the fundamental challenge of NLP: neural networks operate on numbers, but language is made of symbols. We need to convert text into vectors — lists of numbers. The simplest approach is one-hot encoding: if your vocabulary has fifty thousand words, each word becomes a vector with fifty thousand dimensions, all zeros except for a single one at that word's index position. This works mechanically but has a devastating flaw — every word is equally distant from every other word. "King" and "queen" have zero similarity, the same as "king" and "banana." There's no concept of meaning encoded in these vectors. This is what motivates the development of dense embeddings, which we'll explore shortly — representations where similar words actually end up near each other in vector space.

---

## Slide 17: Bag-of-Words and TF/IDF

**Speaker Notes:**
Bag-of-Words is one of the oldest and simplest text representations — just count how many times each word appears in a document. A political article will have high counts for words like "president" and "government," while a science article will show "experiment" and "hypothesis." It's surprisingly effective for topic classification. But it has two major problems: first, common words like "the" and "is" dominate the counts despite carrying no meaning. TF-IDF solves this by weighting each word by how unique it is to that specific document — if "the" appears everywhere, its weight drops to near zero, while distinctive words get amplified. The second problem is more fundamental: bag-of-words completely ignores word order. "I do not like oranges" and "I like oranges" produce nearly identical vectors. This is why we need more sophisticated representations.

---

## Slide 18: Can Animals Be Represented as Vectors?

**Speaker Notes:**
Before we dive into word vectors, let's build intuition with a simpler example from Allison Parrish's excellent tutorial. Imagine representing animals as vectors with just two numbers: a cuteness score and a size score, both from zero to a hundred. A kitten might be 95 cuteness, 15 size. An elephant might be 40 cuteness, 90 size. When you plot these in two-dimensional space, something magical happens — animals that feel similar to us end up close together. A capybara at 70 cuteness, 30 size lands right next to a panda at 74 cuteness, 40 size. And you can do arithmetic: the difference between a tarantula and a hamster — same size but much cuter — when applied to a chicken, gives you a kitten! This analogy reasoning works because meaning is encoded in the directions and distances of the vector space.


---

## Slide 20: Animal Space (1)

**Speaker Notes:**
Let's formalize what we mean by vectors and vector spaces. A vector is just a sequence of numbers — for our animals, it's two numbers representing cuteness and size. A vector space is the collection of all our vectors in the same coordinate system. The powerful insight is that in a well-constructed vector space, geometric proximity corresponds to semantic similarity. Animals that feel similar cluster together; animals that feel different are far apart. But it goes deeper than just distance — the directions in the space encode meaning too. Moving in the "cuteness" direction makes things cuter. Moving in the "size" direction makes things bigger. These directions represent concepts. In word vector spaces with three hundred dimensions, there are hundreds of such meaning-carrying directions, capturing everything from gender to tense to formality — all discovered automatically from data.

---

## Slide 19: Animal Space (2)

**Speaker Notes:**
Let's explore more operations in our animal vector space. Euclidean distance tells us how similar two animals are — capybara and panda are close at distance 11, while tarantula and elephant are far apart at distance 104. The midpoint between chicken and elephant gives us something horse-sized with moderate cuteness — that makes intuitive sense! Vector subtraction captures relationships: the vector from tarantula to hamster represents "same size but much cuter." Apply that same vector to a chicken and you get a kitten. This is analogical reasoning through pure arithmetic — no rules, no logic programming, just vector math. The remarkable thing is that these same operations work identically in 300-dimensional word vector spaces. The math doesn't care whether you have two dimensions or three hundred — distance, midpoint, and analogy all generalize perfectly.


---

## Slide 26: Embeddings

**Speaker Notes:**
Embeddings are one of the most beautiful ideas in NLP. Remember how one-hot encoding made every word equidistant from every other? Embeddings solve this by learning to represent each word as a dense vector of typically 100 to 300 dimensions, where similar words naturally cluster together. Word2Vec, developed at Google in 2013, uses two clever training approaches: either predict a word from its surrounding context, or predict context from a word. The result is a vector space where "king minus man plus woman" actually equals "queen" — the directions in the space encode concepts like gender, royalty, and tense. GloVe from Stanford achieves similar results through co-occurrence statistics. The distributional hypothesis explains why this works: words that appear in similar contexts have similar meanings — and that distributional similarity gets baked directly into the vector geometry.

---

## Slide 27: Language Modeling

**Speaker Notes:**
Language modeling is the key that unlocked modern NLP. The task is deceptively simple: given a sequence of words, predict what comes next. "The cat sat on the ___" — the model learns to predict "mat" or "floor" or "chair." What makes this powerful is that it's self-supervised — you can generate unlimited training data by simply taking existing text and masking words. No human labelers needed. Through this simple objective, the model must learn grammar, facts about the world, reasoning patterns, and even common sense. N-gram models were the earliest approach — just count how often word sequences appear. But neural language models, especially transformers trained on billions of sentences, learn far richer representations. GPT-style models are essentially language models at enormous scale — they predict the next token, and in doing so, learn to perform tasks nobody explicitly trained them for.

---

## Slide 28: Recurrent Neural Networks

**Speaker Notes:**
Standard neural networks take a fixed-size input and produce a fixed-size output — but language is sequential. Word order matters enormously: "dog bites man" versus "man bites dog" are completely different meanings. RNNs solve this by processing one token at a time while maintaining a hidden state — a vector that accumulates information as the network reads through the sequence. Think of it as short-term memory. But basic RNNs have a critical flaw: the vanishing gradient problem means they quickly forget earlier tokens. LSTMs elegantly solve this with three gates — forget, input, and output — that explicitly control what to remember, what to add, and what to output. The forget gate can hold information for hundreds of steps, enabling the network to connect "she" at the end of a paragraph back to "Alice" at the beginning. Bidirectional variants read both forward and backward for even richer context.

---

## Slide 29: Generative Networks

**Speaker Notes:**
So far we've discussed networks that classify or analyze — but some of the most exciting applications generate new content. In NLP, a generative model produces text one word at a time: given everything generated so far, what should the next word be? This autoregressive approach — where each output becomes part of the input for the next step — can produce remarkably fluent and coherent text. RNN-based generators were the first to show this was possible, producing short stories and poetry that sometimes fooled human readers. In computer vision, Generative Adversarial Networks — GANs — use a generator and discriminator competing against each other to produce photorealistic images. The generator creates fake images while the discriminator tries to distinguish real from fake, and this adversarial training produces incredibly realistic outputs. This generative capability is the "Gen" in GenAI.

---

## Slide 30: Attention Mechanisms and Transformers

**Speaker Notes:**
Transformers are arguably the most important architecture in modern AI — they power GPT, BERT, and virtually every large language model. The key problem they solve: RNNs process tokens sequentially, creating a bottleneck that prevents parallelization and struggles with long sequences. Attention, introduced by Bahdanau in 2015, first addressed this by letting the decoder look directly at all encoder states with learned weights — focusing on the most relevant input words for each output word. Transformers took this further by removing recurrence completely. Self-attention lets every token attend to every other token in the same sequence — capturing dependencies regardless of distance. Multi-head attention runs multiple attention patterns in parallel, each learning different types of relationships. And because there's no sequential processing, transformers can train on vastly larger datasets using GPU parallelism. This single architectural change is what made billion-parameter language models practical.

---

## Slide 31: Named Entity Recognition

**Speaker Notes:**
Named Entity Recognition — NER — is one of the most practically useful NLP tasks. Given a sentence like "I need to fly to Paris tomorrow for a meeting with Microsoft," NER identifies Paris as a LOCATION, tomorrow as a DATE, and Microsoft as an ORGANIZATION. This structured extraction turns unstructured text into data that systems can act on — booking flights, scheduling meetings, populating databases. Early NER systems used hand-crafted rules and gazetteers — lists of known entities. Then statistical models like Conditional Random Fields improved accuracy. Today, the state of the art uses transformer models like BERT, fine-tuned on labeled sequences where each token is tagged with its entity type. Bidirectional context is crucial here — knowing that "Apple" is followed by "released a new iPhone" tells you it's a company, not a fruit. This is sequence labeling at its best.

---

## Slide 32: Pre-Trained Large Language Models


**Speaker Notes:**
We've now arrived at the technology that changed everything — pre-trained large language models. BERT, trained by Google on all of Wikipedia plus a book corpus, learns rich bidirectional language representations by predicting randomly masked words. GPT, from OpenAI, learns by predicting the next word in internet text. Both approaches produce models that deeply understand language — grammar, facts, reasoning, style. The revolutionary insight is transfer learning: train one massive model once at enormous cost, then fine-tune it cheaply on any downstream task with just a few hundred labeled examples. Need a spam classifier? Fine-tune BERT with some labeled emails. Need a legal document analyzer? Fine-tune with some annotated contracts. This democratized NLP — you no longer need millions of labeled examples and months of training. The HuggingFace library makes these models available in just a few lines of code, and this is the foundation that generative AI builds upon.

---
