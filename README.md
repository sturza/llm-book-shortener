

# LLM Book Shortener

This project shortens books or long texts using an LLM (Large Language Model).

## Overview

The LLM Book Shortener is a tool designed to condense long texts or books into shorter, more manageable versions. By leveraging Large Language Models such as OpenAI's GPT-4o or others, this tool ensures that the essence of the original text is preserved while reducing its length significantly. The primary goal is to facilitate faster reading and comprehension, making it ideal for students, researchers, and avid readers.

## Motivation

I wrote this to read significantly more and it worked.

## Results

test@MacBook-Pro llm-book-shortener % wc -c waldenrewrite.txt
  231074 waldenrewrite.txt
test@MacBook-Pro llm-book-shortener % wc -c waldenprogress.txt
  636980 waldenprogress.txt

The rewritten version is approximately ~36% from the original. That's a significant reduction.

## Dependencies

- Python 3.10
- OpenAI library (install via pip or similar)
- OpenAI API key

## Usage

### Part 1: Preparing the Text

1. **Add a Text File**: Add a text file containing the book or long text. Optionally, clean it by removing the references section.
2. **Split the Text**: Split the text file using the delimiter `------------`. This can be done around chapter names to divide the book into chapters.
3. **Count Tokens**:
    - Run the first cell labeled "count tokens" in the Jupyter notebook, adjusting the filename to match your text file.
    - The cell will inform you if any chunks exceed 4096 tokens.
4. **Adjust Chunks**:
    - If chunks are larger than 4096 tokens, the script will copy these chunks to a file named `makeshorter.txt`.
    - Go back to the original text file and further split these large chunks using additional `------------` delimiters.
5. **Repeat**:
    - Re-run the "count tokens" cell until it only outputs the number of chunks (e.g., 148 for `walden.txt`).
6. **Clean Up**:
    - Once you have correctly split the text, you can delete the contents of `makeshorter.txt` or adjust the chunk sizes as needed.

### Part 2: Shortening the Text

1. **Add Your OpenAI API Key**: Insert your OpenAI API key in the designated cell.
2. **Set Document Name**: Change the `documentName` variable to match your current filename.
3. **Run the Rewriter**: Execute the cell to start the rewriter and monitor the output.

### Notes

- The rewriter skips parts that are less than 15 tokens, typically chapter titles or similar, to maintain the book's structure.
- The rewriter retries each request up to 5 times before moving on. Adjust this setting if necessary.
- You can stop and resume the rewriter without losing progress, provided you do not alter the original text file and the two files it creates.
- Progress is printed while the rewriter is running.
- The rewritten output file may contain many newlines. You can clean this up by searching for `\n\n\n` and replacing it with `\n\n` until all extra newlines are removed.
- The rewriter uses GPT-4o but can be configured to use any OpenAI model or a compatible LLM that adheres to the OpenAI API.
- Most books fall between a reduction of 40-60%, depending on the content type. I've also managed a 85% reduction for a self help book(without changing anything)
- For getting .txt files use any online converter from .pdf or .epub etc to text - and don't worry about page numbers, text alignment or other non-content artefacts


## Contributing

Contributions are welcome! Please open an issue or submit a pull request with your improvements or suggestions.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Henry David Thoreau for his timeless work, "Walden".
- The open-source community for their valuable tools and libraries.
