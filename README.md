# Language Server Plugin for Patch & CodeMirror 6

This plugin enables custom stateful code completion, hover tooltips, and linter functionality by connecting a CodeMirror 6 editor with a language server over WebSocket.

[How It Works](https://hjr265.me/blog/codemirror-lsp/)

## Usage

```
npm i codemirror-languageserver
```

``` js
import { languageServer } from 'codemirror-languageserver';

const transport = new WebSocketTransport(serverUri)

var ls = languageServer({
	// WebSocket server uri and other client options.
	serverUri,
	rootUri: 'file:///',

	// Alternatively, to share the same client across multiple instances of this plugin.
	client: new LanguageServerClient({
		serverUri,
		rootUri: 'file:///'
	}),

	documentUri: `file:///${filename}`,
	languageId: 'cpp' // As defined at https://microsoft.github.io/language-server-protocol/specification#textDocumentItem.
});

var view = new EditorView({
	state: EditorState.create({
		extensions: [
			// ...
			ls,
			// ...
		]
	})
});
```

- [Toph](https://toph.co): Competitive programming platform. Toph uses Language Server Plugin for CodeMirror 6 with its integrated code editor.

## License

The library is available under the BSD (3-Clause) License.
