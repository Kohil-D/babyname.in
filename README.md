# babyname.in
Baby name suggestions
<DOCTYPE html>
    <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Baby Name Rarity Checker</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-image: url('https://cdnjs.cloudflare.com/ajax/libs/simple-icons/3.0.1/simple-icons.svg');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            position: relative;
        }
        
        body::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(176, 224, 230, 0.8), rgba(255, 182, 193, 0.8));
            z-index: -1;
        }
        
        .container {
            background-color: rgba(255, 255, 255, 0.85);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 900px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            min-height: 500px;
        }
        
        header {
            padding: 20px;
            text-align: center;
            background: linear-gradient(to right, #a6c1ee, #fbc2eb);
            color: white;
        }
        
        h1 {
            font-size: 2.2rem;
            margin-bottom: 5px;
        }
        
        .subtitle {
            font-size: 1rem;
            opacity: 0.9;
        }
        
        .content {
            display: flex;
            flex: 1;
        }
        
        .main-section {
            flex: 1;
            padding: 30px;
            display: flex;
            flex-direction: column;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #555;
        }
        
        input[type="text"], 
        input[type="password"],
        select, 
        textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 1rem;
            background-color: rgba(255, 255, 255, 0.9);
        }
        
        textarea {
            min-height: 100px;
            resize: vertical;
        }
        
        .btn {
            background: linear-gradient(to right, #6a11cb, #2575fc);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            margin-top: 10px;
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .btn:active {
            transform: translateY(0);
        }
        
        .btn-secondary {
            background: linear-gradient(to right, #3498db, #2980b9);
        }
        
        .nav-tabs {
            display: flex;
            list-style: none;
            margin-bottom: 20px;
            border-bottom: 1px solid #ddd;
            flex-wrap: wrap;
        }
        
        .nav-tabs li {
            padding: 10px 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            border-bottom: 2px solid transparent;
            font-weight: 500;
            color: #555;
        }
        
        .nav-tabs li.active {
            border-bottom: 2px solid #6a11cb;
            color: #6a11cb;
            font-weight: 600;
        }
        
        .nav-tabs li:hover {
            background-color: rgba(106, 17, 203, 0.05);
        }
        
        .tab-content {
            flex: 1;
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .result-card {
            background-color: rgba(255, 255, 255, 0.8);
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
        }
        
        .popularity-meter {
            width: 100%;
            height: 10px;
            background-color: #eee;
            border-radius: 5px;
            margin: 15px 0;
            overflow: hidden;
        }
        
        .popularity-level {
            height: 100%;
            width: 0;
            border-radius: 5px;
            transition: width 1s ease-in-out;
        }
        
        .rarity-text {
            font-weight: 600;
            margin-bottom: 10px;
        }
        
        .name-suggestion {
            padding: 12px;
            margin-bottom: 15px;
            border-radius: 8px;
            background-color: rgba(255, 255, 255, 0.8);
            border-left: 4px solid #6a11cb;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .name-suggestion:hover {
            transform: translateX(5px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .name-suggestion h3 {
            margin-bottom: 5px;
            color: #333;
        }
        
        .name-suggestion p {
            color: #666;
            font-size: 0.9rem;
        }
        
        .loading {
            display: none;
            text-align: center;
            padding: 20px;
        }
        
        .loading-spinner {
            border: 4px solid rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            border-top: 4px solid #6a11cb;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 0 auto 20px;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .api-key-section {
            background-color: rgba(255, 255, 255, 0.8);
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 20px;
            border-left: 4px solid #e74c3c;
        }
        
        .code-import {
            margin-top: 20px;
        }
        
        .code-card {
            background-color: rgba(255, 255, 255, 0.8);
            border-radius: 8px;
            padding: 15px;
            margin-top: 15px;
            border-left: 4px solid #3498db;
        }
        
        .code-actions {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            background-color: #2ecc71;
            color: white;
            border-radius: 5px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            z-index: 1000;
            opacity: 0;
            transform: translateY(-20px);
            transition: all 0.3s ease;
        }
        
        .notification.show {
            opacity: 1;
            transform: translateY(0);
        }
        
        .notification.error {
            background-color: #e74c3c;
        }
        
        @media (max-width: 768px) {
            .content {
                flex-direction: column;
            }
            
            .container {
                min-height: auto;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Baby Name Explorer</h1>
            <p class="subtitle">Discover the perfect unique name for your little one</p>
        </header>
        
        <div class="content">
            <div class="main-section">
                <ul class="nav-tabs">
                    <li class="active" data-tab="rarity-checker">Rarity Checker</li>
                    <li data-tab="name-suggestions">Name Suggestions</li>
                    <li data-tab="code-link">Code Link</li>
                    <li data-tab="api-settings">API Settings</li>
                </ul>
                
                <div class="tab-content active" id="rarity-checker">
                    <div class="form-group">
                        <label for="name-input">Enter a name to check its rarity:</label>
                        <input type="text" id="name-input" placeholder="e.g., Oliver, Sophia, etc.">
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
                    
                    <button class="btn" id="check-rarity-btn">Check Rarity</button>
                    
                    <div class="loading" id="rarity-loading">
                        <div class="loading-spinner"></div>
                        <p>Analyzing name data...</p>
                    </div>
                    
                    <div id="rarity-results" style="margin-top: 30px; display: none;">
                        <div class="result-card">
                            <h2 id="result-name"></h2>
                            <p class="rarity-text" id="rarity-text"></p>
                            
                            <div class="popularity-meter">
                                <div class="popularity-level" id="popularity-level"></div>
                            </div>
                            
                            <p id="rarity-details"></p>
                        </div>
                    </div>
                </div>
                
                <div class="tab-content" id="name-suggestions">
                    <div class="form-group">
                        <label for="style-select">Name style preference:</label>
                        <select id="style-select">
                            <option value="unique">Unique & Rare</option>
                            <option value="classic">Classic & Timeless</option>
                            <option value="nature">Nature Inspired</option>
                            <option value="literary">Literary & Artistic</option>
                            <option value="vintage">Vintage Charm</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="gender-select">Gender preference:</label>
                        <select id="gender-select">
                            <option value="neutral">Gender Neutral</option>
                            <option value="boy">Boy Names</option>
                            <option value="girl">Girl Names</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="origin-select">Origin preference (optional):</label>
                        <select id="origin-select">
                            <option value="any">Any Origin</option>
                            <option value="germanic">Germanic</option>
                            <option value="latin">Latin/Roman</option>
                            <option value="greek">Greek</option>
                            <option value="celtic">Celtic/Gaelic</option>
                            <option value="hebrew">Hebrew</option>
                            <option value="scandinavian">Scandinavian</option>
                            <option value="arabic">Arabic</option>
                            <option value="japanese">Japanese</option>
                            <option value="indian">Indian</option>
                        </select>
                    </div>
                    
                    <button class="btn" id="get-suggestions-btn">Get Suggestions</button>
                    
                    <div class="loading" id="suggestions-loading">
                        <div class="loading-spinner"></div>
                        <p>Generating beautiful names for you...</p>
                    </div>
                    
                    <div id="name-suggestions-results" style="margin-top: 30px;"></div>
                </div>
                
                <div class="tab-content" id="code-link">
                    <h2>Import External Code</h2>
                    <p>Link to external code repositories or paste code snippets to enhance this application.</p>
                    
                    <div class="form-group">
                        <label for="code-url">Code Repository URL:</label>
                        <input type="text" id="code-url" placeholder="e.g., https://github.com/username/repo">
                    </div>
                    
                    <div class="form-group">
                        <label for="code-description">Description (what does this code do?):</label>
                        <textarea id="code-description" placeholder="Briefly describe the code functionality..."></textarea>
                    </div>
                    
                    <div class="form-group">
                        <label for="code-snippet">Or paste code snippet directly:</label>
                        <textarea id="code-snippet" placeholder="Paste your code here..."></textarea>
                    </div>
                    
                    <button class="btn" id="link-code-btn">Link Code</button>
                    
                    <div class="code-import">
                        <h3>Linked Code Resources</h3>
                        <div id="linked-code-list">
                            <!-- Linked code will appear here -->
                        </div>
                    </div>
                </div>
                
                <div class="tab-content" id="api-settings">
                    <h2>API Settings</h2>
                    <p>Configure OpenAI API settings to enable name suggestions and analysis.</p>
                    
                    <div class="api-key-section">
                        <p><strong>Note:</strong> Your API key is stored locally in your browser and is never sent to our servers.</p>
                    </div>
                    
                    <div class="form-group">
                        <label for="api-key">OpenAI API Key:</label>
                        <input type="password" id="api-key" placeholder="sk-...">
                    </div>
                    
                    <div class="form-group">
                        <label for="model-select">AI Model:</label>
                        <select id="model-select">
                            <option value="gpt-3.5-turbo">GPT-3.5 Turbo</option>
                            <option value="gpt-4">GPT-4</option>
                            <option value="gpt-4-turbo">GPT-4 Turbo</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="temperature-select">Creativity Level:</label>
                        <select id="temperature-select">
                            <option value="0.3">Conservative (More Common Names)</option>
                            <option value="0.7" selected>Balanced</option>
                            <option value="1.0">Creative (More Unique Names)</option>
                        </select>
                    </div>
                    
                    <button class="btn" id="save-api-settings">Save Settings</button>
                </div>
            </div>
        </div>
    </div>
    
    <div class="notification" id="notification">
        Settings saved successfully!
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize settings from localStorage
            initializeSettings();
            
            // Tab switching functionality
            const tabLinks = document.querySelectorAll('.nav-tabs li');
            const tabContents = document.querySelectorAll('.tab-content');
            
            tabLinks.forEach(link => {
                link.addEventListener('click', function() {
                    // Remove active class from all tabs
                    tabLinks.forEach(tab => tab.classList.remove('active'));
                    tabContents.forEach(content => content.classList.remove('active'));
                    
                    // Add active class to clicked tab
                    this.classList.add('active');
                    const tabId = this.getAttribute('data-tab');
                    document.getElementById(tabId).classList.add('active');
                });
            });
            
            // Name rarity checker functionality
            const checkRarityBtn = document.getElementById('check-rarity-btn');
            checkRarityBtn.addEventListener('click', checkNameRarity);
            
            // Name suggestions functionality
            const getSuggestionsBtn = document.getElementById('get-suggestions-btn');
            getSuggestionsBtn.addEventListener('click', getNameSuggestions);
            
            // API settings save functionality
            const saveApiSettingsBtn = document.getElementById('save-api-settings');
            saveApiSettingsBtn.addEventListener('click', saveApiSettings);
            
            // Code linking functionality
            const linkCodeBtn = document.getElementById('link-code-btn');
            linkCodeBtn.addEventListener('click', linkCode);
            
            // Load any existing linked code
            loadLinkedCode();
            
            // Function to initialize settings
            function initializeSettings() {
                // Load API key and settings from localStorage
                const apiKey = localStorage.getItem('babyNameExplorer_apiKey') || '';
                const model = localStorage.getItem('babyNameExplorer_model') || 'gpt-3.5-turbo';
                const temperature = localStorage.getItem('babyNameExplorer_temperature') || '0.7';
                
                document.getElementById('api-key').value = apiKey;
                document.getElementById('model-select').value = model;
                document.getElementById('temperature-select').value = temperature;
            }
            
            // Function to save API settings
            function saveApiSettings() {
                const apiKey = document.getElementById('api-key').value.trim();
                const model = document.getElementById('model-select').value;
                const temperature = document.getElementById('temperature-select').value;
                
                // Save to localStorage
                localStorage.setItem('babyNameExplorer_apiKey', apiKey);
                localStorage.setItem('babyNameExplorer_model', model);
                localStorage.setItem('babyNameExplorer_temperature', temperature);
                
                // Show notification
                showNotification('Settings saved successfully!');
            }
            
            // Function to show notification
            function showNotification(message, isError = false) {
                const notification = document.getElementById('notification');
                notification.textContent = message;
                
                if (isError) {
                    notification.classList.add('error');
                } else {
                    notification.classList.remove('error');
                }
                
                notification.classList.add('show');
                
                setTimeout(() => {
                    notification.classList.remove('show');
                }, 3000);
            }
            
            // Function to check name rarity using AI API
            async function checkNameRarity() {
                const nameInput = document.getElementById('name-input').value.trim();
                const region = document.getElementById('region-select').value;
                
                if (!nameInput) {
                    showNotification('Please enter a name first!', true);
                    return;
                }
                
                const apiKey = localStorage.getItem('babyNameExplorer_apiKey');
                if (!apiKey) {
                    showNotification('Please set your OpenAI API key in API Settings tab', true);
                    document.querySelector('[data-tab="api-settings"]').click();
                    return;
                }
                
                // Show loading indicator
                document.getElementById('rarity-loading').style.display = 'block';
                document.getElementById('rarity-results').style.display = 'none';
                
                try {
                    // First try to use the actual API
                    const rarityData = await fetchNameRarityFromAPI(nameInput, region);
                    updateRarityResults(nameInput, rarityData);
                } catch (error) {
                    console.error('API Error:', error);
                    // Fallback to simulated data if API fails
                    const simulatedData = getSimulatedRarityData(nameInput, region);
                    updateRarityResults(nameInput, simulatedData);
                }
            }
            
            // Function to update the UI with rarity results
            function updateRarityResults(name, rarityData) {
                document.getElementById('result-name').textContent = name;
                document.getElementById('rarity-text').textContent = rarityData.rarityText;
                document.getElementById('rarity-details').textContent = rarityData.details;
                
                const popularityLevel = document.getElementById('popularity-level');
                popularityLevel.style.width = `${rarityData.popularityPercentage}%`;
                popularityLevel.style.backgroundColor = getColorForPopularity(rarityData.popularityPercentage);
                
                // Hide loading and show results
                document.getElementById('rarity-loading').style.display = 'none';
                document.getElementById('rarity-results').style.display = 'block';
            }
            
            // Function to get name suggestions using AI API
            async function getNameSuggestions() {
                const style = document.getElementById('style-select').value;
                const gender = document.getElementById('gender-select').value;
                const origin = document.getElementById('origin-select').value;
                
                const apiKey = localStorage.getItem('babyNameExplorer_apiKey');
                if (!apiKey) {
                    showNotification('Please set your OpenAI API key in API Settings tab', true);
                    document.querySelector('[data-tab="api-settings"]').click();
                    return;
                }
                
                // Show loading indicator
                document.getElementById('suggestions-loading').style.display = 'block';
                document.getElementById('name-suggestions-results').innerHTML = '';
                
                try {
                    // First try to use the actual API
                    const suggestions = await fetchNameSuggestionsFromAPI(style, gender, origin);
                    updateSuggestionsResults(suggestions);
                } catch (error) {
                    console.error('API Error:', error);
                    // Fallback to simulated data if API fails
                    const simulatedSuggestions = getSimulatedNameSuggestions(style, gender);
                    updateSuggestionsResults(simulatedSuggestions);
                }
            }
            
            // Function to update the UI with suggestion results
            function updateSuggestionsResults(suggestions) {
                const suggestionsContainer = document.getElementById('name-suggestions-results');
                suggestionsContainer.innerHTML = '';
                
                suggestions.forEach(suggestion => {
                    const suggestionElement = document.createElement('div');
                    suggestionElement.className = 'name-suggestion';
                    suggestionElement.innerHTML = `
                        <h3>${suggestion.name}</h3>
                        <p>${suggestion.meaning}</p>
                        <p><strong>Origin:</strong> ${suggestion.origin}</p>
                        <p><strong>Rarity:</strong> ${suggestion.rarity}</p>
                    `;
                    suggestionsContainer.appendChild(suggestionElement);
                });
                
                // Hide loading
                document.getElementById('suggestions-loading').style.display = 'none';
            }
            
            // Function to link external code
            function linkCode() {
                const codeUrl = document.getElementById('code-url').value.trim();
                const codeDescription = document.getElementById('code-description').value.trim();
                const codeSnippet = document.getElementById('code-snippet').value.trim();
                
                if ((!codeUrl || !codeDescription) && !codeSnippet) {
                    showNotification('Please provide either a URL with description or a code snippet', true);
                    return;
                }
                
                // Create a new linked code object
                const linkedCode = {
                    id: Date.now(),
                    url: codeUrl,
                    description: codeDescription,
                    snippet: codeSnippet,
                    timestamp: new Date().toLocaleString()
                };
                
                // Get existing linked code from localStorage
                let linkedCodeList = JSON.parse(localStorage.getItem('babyNameExplorer_linkedCode')) || [];
                
                // Add new linked code
                linkedCodeList.push(linkedCode);
                
                // Save to localStorage
                localStorage.setItem('babyNameExplorer_linkedCode', JSON.stringify(linkedCodeList));
                
                // Clear form
                document.getElementById('code-url').value = '';
                document.getElementById('code-description').value = '';
                document.getElementById('code-snippet').value = '';
                
                // Reload linked code list
                loadLinkedCode();
                
                // Show notification
                showNotification('Code linked successfully!');
            }
            
            // Function to load linked code from localStorage
            function loadLinkedCode() {
                const linkedCodeList = JSON.parse(localStorage.getItem('babyNameExplorer_linkedCode')) || [];
                const linkedCodeContainer = document.getElementById('linked-code-list');
                
                if (linkedCodeList.length === 0) {
                    linkedCodeContainer.innerHTML = '<p>No code resources linked yet.</p>';
                    return;
                }
                
                linkedCodeContainer.innerHTML = '';
                
                linkedCodeList.forEach(code => {
                    const codeElement = document.createElement('div');
                    codeElement.className = 'code-card';
                    
                    let codeContent = '';
                    
                    if (code.url) {
                        codeContent += `
                            <h4><a href="${code.url}" target="_blank">${code.url}</a></h4>
                            <p>${code.description}</p>
                        `;
                    }
                    
                    if (code.snippet) {
                        codeContent += `
                            <details>
                                <summary>View Code Snippet</summary>
                                <pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; overflow-x: auto;">${code.snippet}</pre>
                            </details>
                        `;
                    }
                    
                    codeContent += `
                        <p><small>Added on: ${code.timestamp}</small></p>
                        <div class="code-actions">
                            <button class="btn btn-secondary delete-code" data-id="${code.id}">Delete</button>
                        </div>
                    `;
                    
                    codeElement.innerHTML = codeContent;
                    linkedCodeContainer.appendChild(codeElement);
                });
                
                // Add event listeners for delete buttons
                document.querySelectorAll('.delete-code').forEach(button => {
                    button.addEventListener('click', function() {
                        const codeId = parseInt(this.getAttribute('data-id'));
                        deleteLinkedCode(codeId);
                    });
                });
            }
            
            // Function to delete linked code
            function deleteLinkedCode(codeId) {
                let linkedCodeList = JSON.parse(localStorage.getItem('babyNameExplorer_linkedCode')) || [];
                
                // Filter out the code to delete
                linkedCodeList = linkedCodeList.filter(code => code.id !== codeId);
                
                // Save to localStorage
                localStorage.setItem('babyNameExplorer_linkedCode', JSON.stringify(linkedCodeList));
                
                // Reload linked code list
                loadLinkedCode();
                
                // Show notification
                showNotification('Code resource deleted');
            }
            
            // Function to fetch name rarity data from OpenAI API
            async function fetchNameRarityFromAPI(name, region) {
                const apiKey = localStorage.getItem('babyNameExplorer_apiKey');
                const model = localStorage.getItem('babyNameExplorer_model') || 'gpt-3.5-turbo';
                
                const prompt = `
                    You are a baby name expert with access to comprehensive global naming databases.
                    Please analyze the name "${name}" in ${getRegionName(region)}.
                    
                    Provide the following information in JSON format:
                    1. rarityText: A categorical assessment (Very Rare, Rare, Moderately Common, Common, or Very Common)
                    2. details: 1-2 sentences about the name's popularity, usage, and any interesting trends
                    3. popularityPercentage: A number between 0-100 representing how common the name is (0 = extremely rare, 100 = extremely common)
                    
                    Return ONLY valid JSON without any explanation or additional text.
                `;
                
                try {
                    const response = await fetch('https://api.openai.com/v1/chat/completions', {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json',
                            'Authorization': `Bearer ${apiKey}`
                        },
                        body: JSON.stringify({
                            model: model,
                            messages: [
                                {
                                    role: 'system',
                                    content: 'You are a helpful baby name analysis assistant that returns only JSON data.'
                                },
                                {
                                    role: 'user',
                                    content: prompt
                                }
                            ],
                            temperature: 0.3
                        })
                    });
                    
                    if (!response.ok) {
                        throw new Error(`API request failed with status ${response.status}`);
                    }
                    
                    const data = await response.json();
                    const content = data.choices[0].message.content;
                    
                    // Extract JSON from response (handles cases where the AI might include backticks or explanations)
                    const jsonMatch = content.match(/\{[\s\S]*\}/);
                    if (jsonMatch) {
                        return JSON.parse(jsonMatch[0]);
                    } else {
                        throw new Error('Failed to parse JSON from API response');
                    }
                } catch (error) {
                    console.error('Error calling OpenAI API:', error);
                    throw error;
                }
            }
            
            // Function to fetch name suggestions from OpenAI API
            async function fetchNameSuggestionsFromAPI(style, gender, origin) {
                const apiKey = localStorage.getItem('babyNameExplorer_apiKey');
                const model = localStorage.getItem('babyNameExplorer_model') || 'gpt-3.5-turbo';
