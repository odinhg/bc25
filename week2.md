# Week 2 – Categories and Functors – Part 1

### Categories

A category $\mathcal{C}$ consists of:

- A class of objects $\textbf{Ob}(\mathcal{C})$ or simply $\mathcal{C}$.
- For each pair of objects $A,B\in\mathcal{C}$, a set of morphisms from $A$ to $B$, denoted $\mathcal{C}(A,B)$ or $\hom_\mathcal{C}(A,B)$.
- For each object $A\in\mathcal{C}$, an identity morphism $\textbf{id}_A\in\mathcal{C}(A,A)$.
- For each triple of objects $A,B,C\in\mathcal{C}$, a composition function $\circ:\mathcal{C}(B,C)\times\mathcal{C}(A,B)\to\mathcal{C}(A,C)$. This function is associative and has identities as neutral elements.

By associativity, we mean that for all $f\in\mathcal{C}(A,B)$, $g\in\mathcal{C}(B,C)$, and $h\in\mathcal{C}(C,D)$, we have $h\circ(g\circ f) = (h\circ g)\circ f$. So no parentheses are needed.

Identities are neutral elements in the sense that for all $f\in\mathcal{C}(A,B)$, we have $f\circ\textbf{id}_A = f = \textbf{id}_B\circ f$.

**Note:** I write that $\mathcal{C}(A,B)$ is a set, but it could be a class. When it is a set, the category is called locally small.

#### Example – Opposite category

Given a category $\mathcal{C}$, the opposite category $\mathcal{C}^\text{op}$ has the same objects but reversed morphisms. That is, $\mathcal{C}^\text{op}(A,B) = \mathcal{C}(B,A)$. Composition is also reversed in the sense that $f\circ_{\mathcal{C}^\text{op}} g = g\circ_\mathcal{C} f$.

#### Example – The category of sets

The category of sets $\mathbf{Set}$ has sets as objects and functions as morphisms. The identity morphism is the identity function, and composition is function composition.

It has initial and terminal objects, the empty set and singletons, respectively. It has products and coproducts, the cartesian product and disjoint unions, respectively. It has exponentials, the set of functions.

#### Example - The category of sets with relations

The category of sets with relations $\mathbf{Rel}$ has sets as objects and relations as morphisms. The identity morphism is the identity relation, and composition is relational composition.

Both the initial and terminal objects are the empty set. 


#### Example – The category of groups

The category of groups $\mathbf{Grp}$ has groups as objects and group homomorphisms as morphisms. The products are the direct products, and the coproducts are the free products.

#### Example – Group as a category

A group $G$ can be seen as a category with a single object $G$ and morphisms the elements of $G$. Composition is the group operation, and the identity morphism is the identity element.


### Epimorphisms and monomorphisms

#### Epimorphisms

A morphism $f:A\to B$ is an epimorphism if for all objects $Z$ and morphisms $g,h:B\to Z$, we have $g\circ f = h\circ f$ implies $g = h$.

#### Monomorphisms

A morphism $f:A\to B$ is a monomorphism if for all objects $Z$ and morphisms $g,h:Z\to A$, we have $f\circ g = f\circ h$ implies $g = h$.

Using the notion of the opposite category, we can define monomorphisms as epimorphisms in $\mathcal{C}^\text{op}$, and vice versa.

**Example:** In $\mathbf{Set}$, monomorphisms are injective functions, and epimorphisms are surjective functions. In $\mathbf{Grp}$, monomorphisms are injective group homomorphisms, and epimorphisms are surjective group homomorphisms.


#### Isomorphisms

A morphism $f:A\to B$ is an isomorphism if there exists a morphism $g:B\to A$ such that $g\circ f = \textbf{id}_A$ and $f\circ g = \textbf{id}_B$. In this case, $g$ is also an isomorphism, and we say that $A$ and $B$ are isomorphic (objects).

**Warning:** Even if $f$ is both an epimorphism and a monomorphism, it might not be an isomorphism. Consider the category with two objects $\{a,b\}$ and a single morphism $f:a\to b$ (in addition to the identity morphisms). This morphism is both an epimorphism and a monomorphism, but it is not an isomorphism.

**But:** If $f\colon A\to B$ is an isomorphism, then $f$ is both an epimorphism and a monomorphism. We prove $f$ is an epimorphism, let $g\colon B\to A$ be the inverse of $f$. Let $a,b\colon B\to Z$ be morphisms such that $a\circ f = b\circ f$. Then $a\circ f\circ g = b\circ f\circ g$, so $a = b$. The proof that $f$ is a monomorphism is similar.

**Remark:** A category where all morphisms are isomorphisms is called a groupoid.


### Products and coproducts

#### Products

Given objects $A$ and $B$, a product is an object $A\times B$ together with morphisms $\pi_A:A\times B\to A$ and $\pi_B:A\times B\to B$ such that for all objects $Z$ and morphisms $f:Z\to A$ and $g:Z\to B$, there exists a unique morphism $h:Z\to A\times B$ such that $f = \pi_A\circ h$ and $g = \pi_B\circ h$.

Intuitively, every candidate for $A\times B$ should factor uniquely through the projections. 
#### Coproducts

Given objects $A$ and $B$, a coproduct is an object $A\amalg B$ together with morphisms $\iota_A:A\to A\amalg B$ and $\iota_B:B\to A\amalg B$ such that for all objects $Z$ and morphisms $f:A\to Z$ and $g:B\to Z$, there exists a unique morphism $h:A\amalg B\to Z$ such that $f = h\circ\iota_A$ and $g = h\circ\iota_B$.

We can also define coproducts as products in the opposite category, and vice versa. 

### Exponential objects

Given objects $A$ and $B$, an exponential object $B^A$ is an object together with a morphism $\textbf{ev}:B^A\times A\to B$ such that for all objects $Z$ and morphisms $f:Z\times A\to B$, there exists a unique morphism $h:Z\to B^A$ such that $f = \textbf{ev}\circ(h\times\textbf{id}_A)$.


### Functors

A functor $F:\mathcal{C}\to\mathcal{D}$ between categories $\mathcal{C}$ and $\mathcal{D}$ maps objects to objects and morphisms to morphisms. It also preserves identities and composition.

For all morphisms $f:A\to B$, we have $F(f):F(A)\to F(B)$. For all objects $A\in\mathcal{C}$, we have $F(\textbf{id}_A) = \textbf{id}_{F(A)}$. For all morphisms $f:A\to B$ and $g:B\to C$, we have $F(g\circ f) = F(g)\circ F(f)$.

**Note:** Functors preserve commutative diagrams.


