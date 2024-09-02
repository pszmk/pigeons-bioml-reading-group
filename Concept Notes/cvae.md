$$\log p(x | C) \rightarrow \text{ELBO} = \mathbb{E}_{q_\phi(z|x)} \left [ \log p_\theta(x|z, C) \right ] - \mathbb{D}_{\text{KL}} \left [ q_\phi(z| x) \, || \, p(z | C) \right ]$$
$$p_\theta(x|z, C) = p_\theta(x, C | z) \cdot p(z) \cdot \frac{1}{p(z | C) \cdot p(C)}$$
---
$$p(c_1) = \mathbb{E}_{p(c_2)} \left [ p(c_1 | c_2) \right ]$$
$$ \mathbb{E}_{p(c_2)} \left [ p(z | c_1, c_2) \right ] = \mathbb{E}_{p(c_2)} \left [ \frac{p(z , c_1, c_2)}{p(c_1, c_2)} \right ] = \mathbb{E}_{p(c_2)} \left [ \frac{p(z, c_2 | c_1)}{p(c_2 | c_1)} \right ] $$

$$ \mathbb{E}_{p(c_2 | c_1)} \left [ p(z | c_1, c_2) \right ] = \mathbb{E}_{p(c_2 | c_1)} \left [ \frac{p(z , c_1, c_2)}{p(c_1, c_2)} \right ] = \mathbb{E}_{p(c_2 | c_1)} \left [ \frac{p(z, c_2 | c_1)}{p(c_2 | c_1)} \right ] = p(z|c_1) $$
// When $x$ contains full information about $c_1$:
$$ p(c_1) = \mathbb{E}_x [ p(c_1 | x) ]$$
$$ \mathbb{E}_{p(c_2 | c_1)} \left[ \frac{p(z, c_1, c_2)}{p(c_1, c_2)} \right] = \mathbb{E}_{p(z | c_1)} [ \mathbb{E}_{p_\theta(x | z, c_1)} [ \mathbb{E}_{q_\phi(z | x)} [...] ] ] $$
we want to 
## Bullet points
- 

## Questions
1. 

## References / Note links
1. 