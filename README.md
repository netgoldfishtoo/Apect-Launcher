<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Apect Launcher - Build Guide</title>
    <style>
        :root {
            --bg-color: #0d1117;
            --container-bg: #161b22;
            --text-main: #c9d1d9;
            --text-bright: #f0f6fc;
            --accent-purple: #bc8cff;
            --accent-blue: #58a6ff;
            --accent-green: #3fb950;
            --accent-orange: #f0883e;
            --border-color: #30363d;
            --code-bg: #010409;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            line-height: 1.6;
            margin: 0;
            padding: 40px 20px;
            display: flex;
            justify-content: center;
        }

        .container {
            max-width: 850px;
            width: 100%;
            background-color: var(--container-bg);
            padding: 40px;
            border-radius: 12px;
            border: 1px solid var(--border-color);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        header {
            text-align: center;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 30px;
            margin-bottom: 30px;
        }

        h1 {
            color: var(--accent-purple);
            font-size: 2.5rem;
            margin-bottom: 10px;
        }

        .subtitle {
            font-style: italic;
            color: var(--text-main);
            font-size: 1.1rem;
            margin-bottom: 20px;
        }

        .badges {
            display: flex;
            justify-content: center;
            gap: 10px;
            flex-wrap: wrap;
        }

        .badge {
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: bold;
            color: white;
        }

        h2 {
            color: var(--accent-blue);
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 8px;
            margin-top: 40px;
        }

        h3 {
            color: var(--accent-purple);
            margin-top: 25px;
        }

        code {
            background-color: var(--code-bg);
            padding: 0.2em 0.4em;
            border-radius: 6px;
            font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
            font-size: 90%;
        }

        pre {
            background-color: var(--code-bg);
            padding: 16px;
            border-radius: 8px;
            border: 1px solid var(--border-color);
            overflow-x: auto;
        }

        pre code {
            background-color: transparent;
            padding: 0;
            color: #d1d5da;
        }

        .callout {
            padding: 16px;
            margin: 20px 0;
            border-radius: 8px;
            border-left: 5px solid;
        }

        .important {
            background-color: rgba(88, 166, 255, 0.1);
            border-color: var(--accent-blue);
        }

        .tip {
            background-color: rgba(63, 185, 80, 0.1);
            border-color: var(--accent-green);
        }

        .important-title { color: var(--accent-blue); font-weight: bold; display: block; margin-bottom: 5px; }
        .tip-title { color: var(--accent-green); font-weight: bold; display: block; margin-bottom: 5px; }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }

        table th, table td {
            text-align: left;
            padding: 12px;
            border: 1px solid var(--border-color);
        }

        table th {
            background-color: var(--code-bg);
            color: var(--accent-purple);
        }

        footer {
            margin-top: 50px;
            text-align: center;
            font-size: 0.9rem;
            color: #8b949e;
        }

        a {
            color: var(--accent-blue);
            text-decoration: none;
        }

        a:hover {
            text-decoration: underline;
        }

        ul {
            padding-left: 20px;
        }

        li {
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>🌌 Apect Launcher</h1>
        <div class="subtitle">Next-Generation Performance. Sleek Aesthetics.</div>
        <div class="badges">
            <span class="badge" style="background-color: #f0883e;">Rust</span>
            <span class="badge" style="background-color: #bc8cff;">Linux | Windows</span>
            <span class="badge" style="background-color: #3fb950;">License: MIT</span>
        </div>
    </header>

    <p>Welcome to the <strong>Apect Launcher</strong> build guide. This document provides a comprehensive walkthrough for setting up your environment and building the launcher from scratch.</p>

    <h2>🚀 Getting Started</h2>

    <h3>1. The Rust Toolchain</h3>
    <p>Apect is built using the Rust programming language. The recommended way to manage your Rust installation is through <code>rustup</code>.</p>

    <h4>Linux (Mint, Ubuntu) & macOS</h4>
    <p>Open your terminal and execute:</p>
    <pre><code>curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh</code></pre>

    <div class="callout important">
        <span class="important-title">⚠️ IMPORTANT</span>
        After installation, restart your terminal or run <code>source $HOME/.cargo/env</code> to initialize the toolchain in your current session.
    </div>

    <h4>Windows</h4>
    <ul>
        <li>Download the <a href="https://rustup.rs/">rustup-init.exe</a>.</li>
        <li><strong>Requirement:</strong> Ensure you have the <a href="https://visualstudio.microsoft.com/visual-cpp-build-tools/">C++ build tools for Visual Studio</a> installed.</li>
    </ul>

    <h2>📦 System Dependencies</h2>
    <p>To handle the GUI rendering and secure networking, certain system-level libraries are required.</p>

    <h3>Linux (Debian/Ubuntu/Mint)</h3>
    <p>Run the following command to install the necessary build tools and development headers:</p>
    <pre><code>sudo apt update && sudo apt install -y \
  build-essential \
  pkg-config \
  libssl-dev \
  libdbus-1-dev \
  libgtk-3-dev</code></pre>

    <h2>🛠️ Compilation & Installation</h2>

    <h3>Clone the Repository</h3>
    <pre><code>git clone https://github.com/netgoldfishtoo/Apect-Launcher/
cd Apect-Launcher</code></pre>

    <h3>Execution Modes</h3>
    <table>
        <thead>
            <tr>
                <th>Mode</th>
                <th>Command</th>
                <th>Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td><strong>Development</strong></td>
                <td><code>cargo run</code></td>
                <td>Fastest compile time. Includes debug symbols.</td>
            </tr>
            <tr>
                <td><strong>Release</strong></td>
                <td><code>cargo run --release</code></td>
                <td>Optimized for performance and lower memory usage.</td>
            </tr>
        </tbody>
    </table>

    <div class="callout tip">
        <span class="tip-title">💡 TIP</span>
        The first build will download approximately <strong>900+ dependencies</strong>. This process is only required once; subsequent builds will be near-instant.
    </div>

    <h2>📂 Locating the Binary</h2>
    <p>Once compiled in <strong>Release Mode</strong>, your production-ready executable can be found at:</p>
    <code>./target/release/apect</code>

    <h2>🧪 Troubleshooting</h2>
    <p>If you encounter an <strong>Internal Compiler Error (ICE)</strong> during the compilation, a clean state usually resolves it:</p>
    <pre><code>cargo clean
cargo run</code></pre>

    <footer>
        Built with ❤️ using the <a href="https://www.rust-lang.org/">Rust Programming Language</a>
    </footer>
</div>

</body>
</html>
