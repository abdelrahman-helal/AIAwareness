# AI Sentiment Analysis on Company Personas

## Overview

Inspired by Anthropic's economic index report—which highlights that large companies often use AI for augmenting engineers' work, while startups tend to use AI for automation—this project investigates sentiment bias in AI-generated responses. Specifically, it analyzes the positive sentiment in responses from Google's Gemini AI to the prompt:

> "Describe in one paragraph to what extent the company can rely on AI tools for its software projects."

The analysis explores whether Gemini's responses differ based on the persona it is asked to emulate.

## Methodology

- **Personas:** The AI was prompted to answer as either a "Google CEO" or a "Startup founder," chosen at random.
- **Sentiment Analysis:** Each response was scored for positive sentiment using a sentiment analysis model.
- **Hypothesis Testing** Null hypothesis: There is no difference in the average positive sentiment score between the "Google CEO" and "Startup founder" personas ($\mu_{g} - \mu_{s} = 0$)
Alternative hypothesis: There is a difference in the average positive sentiment score between the "Google CEO" and "Startup founder" personas ($\mu_{g} - \mu_{s} \neq 0$).  
- **Statistical Testing:** The average positive sentiment scores for each persona were compared, and we conducted a two-tail t-test to assess the p-value.

## Key Findings

- The average positive sentiment score for the "Google CEO" persona was significantly higher than that for the "Startup founder" persona (p-value << 0.05).
- This raised the hypothesis that Gemini, being a Google product, might exhibit inherent bias toward Google.
- To test this, the analysis was extended to compare responses as "Google CEO" versus "Microsoft CEO."
- The results showed highly overlapping confidence intervals and a non-significant difference (p = 0.78), suggesting no strong inherent bias toward Google in this context.

## Conclusion

The project demonstrates a systematic approach to probing potential AI bias in sentiment, using persona-based prompting and statistical analysis. While initial results suggested a possible bias, further testing with a different comparison group (Microsoft CEO) did not support this hypothesis.

## How to Run

1. Install dependencies:
    ```bash
    pip install torch torchvision torchaudio google-generativeai python-dotenv
    ```
2. Set up your Gemini API key in a `.env` file:
    ```
    GEMINI_API_KEY=your_api_key_here
    ```
3. Run the notebook `Analysis.ipynb` to reproduce the analysis and plots.

## Disclaimer

This project is a curiosity-driven exploration and should not be considered as an evidence of AI bias. There may be other factors influencing the AI's responses as well, and the sentiment analysis may not fully capture the nuances in the responses, espeically since all responses fall in the positive regime. 