# babyname.in
Baby name suggestions
<DOCTYPE html>
    <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Baby Name Explorer</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <header>
            <h1>Baby Name Explorer</h1>
            <p>Discover the perfect name for your little one</p>
        </header>

        <div id="notification" class="notification"></div>

        <nav>
            <ul class="nav-tabs">
                <li class="active" data-tab="rarity-checker">Rarity Checker</li>
                <li data-tab="name-suggestions">Name Suggestions</li>
                <li data-tab="api-settings">Settings</li>
                <li data-tab="code-linking">Code Resources</li>
            </ul>
        </nav>

        <div class="tab-content active" id="rarity-checker">
            <h2>Name Rarity Checker</h2>
            <div class="form-group">
                <label for="name-input">Enter a name:</label>
                <input type="text" id="name-input" placeholder="Enter a name">
            </div>
            <div class="form-group">
                <label for="region-select">Select region:</label>
                <select id="region-select">
                    <option value="usa">United States</option>
                    <option value="uk">United Kingdom</option>
                    <option value="canada">Canada</option>
                    <option value="australia">Australia</option>
                    <option value="global">Global</option>
                </select>
            </div>
            <button id="check-rarity-btn" class="btn btn-primary">Check Rarity</button>

            <div id="rarity-loading" class="loading-spinner" style="display: none;">
                <div class="spinner"></div>
                <p>Analyzing name...</p>
            </div>

            <div id="rarity-results" style="display: none;">
                <h3><span id="result-name"></span>: <span id="rarity-text"></span></h3>
                <div class="popularity-bar">
                    <div id="popularity-level" class="popularity-level"></div>
                </div>
                <p id="rarity-details"></p>
            </div>
        </div>

        <div class="tab-content" id="name-suggestions">
            <h2>Name Suggestions</h2>
            <div class="form-group">
                <label for="style-select">Style:</label>
                <select id="style-select">
                    <option value="unique">Unique</option>
                    <option value="classic">Classic</option>
                    <option value="nature">Nature-inspired</option>
                    <option value="literary">Literary</option>
                </select>
            </div>
            <div class="form-group">
                <label for="gender-select">Gender:</label>
                <select id="gender-select">
                    <option value="neutral">Gender Neutral</option>
                    <option value="boy">Boy</option>
                    <option value="girl">Girl</option>
                </select>
            </div>
            <div class="form-group">
                <label for="origin-select">Origin:</label>
                <select id="origin-select">
                    <option value="any">Any</option>
                    <option value="english">English</option>
                    <option value="greek">Greek</option>
                    <option value="latin">Latin</option>
                    <option value="hebrew">Hebrew</option>
                    <option value="celtic">Celtic</option>
                </select>
            </div>
            <button id="get-suggestions-btn" class="btn btn-primary">Get Suggestions</button>

            <div id="suggestions-loading" class="loading-spinner" style="display: none;">
                <div class="spinner"></div>
                <p>Finding perfect names...</p>
            </div>

            <div id="name-suggestions-results" class="suggestion-container"></div>
        </div>

        <div class="tab-content" id="api-settings">
            <h2>API Settings</h2>
            <div class="api-key-section">
                <div class="form-group">
                    <label for="api-key">OpenAI API Key (optional):</label>
                    <input type="password" id="api-key" placeholder="sk-...">
                    <p class="helper-text">Your API key is stored locally and never sent to our servers.</p>
                </div>
                <div class="form-group">
                    <label for="model-select">Model:</label>
                    <select id="model-select">
                        <option value="gpt-3.5-turbo">GPT-3.5 Turbo (Faster)</option>
                        <option value="gpt-4">GPT-4 (More Accurate)</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="temperature-select">Creativity Level:</label>
                    <select id="temperature-select">
                        <option value="0.3">Low - More predictable results</option>
                        <option value="0.7" selected>Medium - Balanced creativity</option>
                        <option value="1.0">High - More varied results</option>
                    </select>
                </div>
            </div>
            <button id="save-api-settings" class="btn btn-primary">Save Settings</button>
        </div>

        <div class="tab-content" id="code-linking">
            <h2>Link Code Resources</h2>
            <p>Save code snippets, examples, or links to useful resources.</p>
            
            <div class="form-group">
                <label for="code-url">Resource URL (optional):</label>
                <input type="text" id="code-url" placeholder="https://...">
            </div>
            <div class="form-group">
                <label for="code-description">Description (optional):</label>
                <input type="text" id="code-description" placeholder="Brief description...">
            </div>
            <div class="form-group">
                <label for="code-snippet">Code Snippet (optional):</label>
                <textarea id="code-snippet" placeholder="Paste code here..."></textarea>
            </div>
            <button id="link-code-btn" class="btn btn-primary">Save Resource</button>
            
            <h3>Linked Resources</h3>
            <div id="linked-code-list" class="linked-code-container">
                <p>No code resources linked yet.</p>
            </div>
        </div>
    </div>

    <footer>
        <p>Baby Name Explorer - A tool for finding the perfect baby name</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>
