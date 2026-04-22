## Cross-Domain Inference: Twitter Results

To see how well our model could handle a different type of text, we tested **CyNER Model 2** on Twitter data. This was a tough test because the model was trained on cybersecurity reports, while Twitter is much more informal and uses very different kinds of entities. Our model was trained to find **Malware, Indicator, System, Organization, and Vulnerability**, while Twitter data usually has more general entity types like **person, organization, and location**.

### What we noticed from the outputs
After looking through the predictions, it was pretty clear that the model does not transfer well to Twitter. That makes sense, since it learned patterns from cybersecurity text instead of social media language. On Twitter, the model often tries to force words into one of its cybersecurity labels. For example, some platform or device names may get labeled as **System**, and some hashtags, acronyms, or unusual strings may get labeled as **Malware**. At the same time, labels like **Indicator** and **Vulnerability** almost never show up because those are much more specific to cybersecurity reports.

### What the numbers show
The numbers support what we saw in the examples. Model 2 had a higher **detection rate** than the pretrained baseline, **34.1% compared to 20.5%**, which means it was more likely to tag Twitter entity tokens as some kind of entity.

But that does **not** mean it actually performed better on Twitter. Almost all of Model 2’s predictions were labeled as **Malware** (**96.8%**), which shows that it was mostly using the wrong category. So even though it was tagging more tokens, it was not identifying them in a meaningful way for this dataset.

The **92.9% token-level agreement** with the baseline also sounds stronger than it really is. In NER, most tokens are not entities, so high agreement often just means both models are saying “not an entity” on the same words.

### Overall takeaway
Overall, this shows that **CyNER Model 2 works much better in its own cybersecurity domain than it does on general Twitter text**. We see that as a good sign, because it suggests the model actually learned domain-specific patterns instead of acting like a general-purpose NER model.
