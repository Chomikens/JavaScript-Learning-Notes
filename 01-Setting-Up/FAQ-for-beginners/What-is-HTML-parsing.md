# How HTML parsing process look like? 


HTML parsing is the process by which web browsers interpret and convert the HTML (HyperText Markup Language) code of a webpage into a Document Object Model (DOM) tree structure that the browser can understand and render on the screen. This process is critical for displaying web pages correctly, as it translates the markup (tags, attributes, content, etc.) into a form that browsers can render for users.

Here’s a step-by-step overview of how HTML parsing works:

1.**Tokenization**: The browser reads the raw HTML text and converts it into recognizable tokens, such as start tags, end tags, attribute names, and attribute values. This step breaks down the HTML into its basic components.
    
2.**Tree Construction**: Using the tokens generated in the tokenization step, the browser starts building the DOM tree. This tree represents the hierarchical structure of the HTML document, with each node in the tree corresponding to an element (or part) of the document. For example, a `<div>` tag in your HTML would become a `div` node in the DOM tree.

2a. **CSSOM Construction**: Parallel to DOM tree construction, the browser also builds the CSS Object Model (CSSOM) based on the stylesheets linked or embedded in the HTML. The CSSOM represents all the CSS selectors and properties applicable to the document.
    
3.**Handling JavaScript**: If the parser encounters a `<script>` tag during parsing, it needs to handle it according to the attributes (`async`, `defer`, or neither) of the script. This can affect the parsing process:
    
    -   **No Attributes (Blocking)**: By default, the HTML parser stops and must execute the script before it can continue parsing the rest of the HTML document. This behavior blocks the parsing process.
    -   **Async**: The script is downloaded asynchronously, and the HTML parser continues its work. The script will be executed as soon as it's downloaded, which might interrupt the parsing.
    -   **Defer**: The script is downloaded asynchronously, but its execution is deferred until after the HTML parsing is complete. This does not block the HTML parser.

4.**Render Tree Construction**: Once the DOM and CSSOM are constructed, the browser combines them into the render tree, which represents only those nodes that will be rendered on the page, along with their styling information.
    
5.**Layout**: The browser calculates the layout (or reflow) for each visible element, determining their exact position and size on the page.
    
6.**Painting**: Finally, the browser paints the content on the screen, following the layout calculated in the previous step.