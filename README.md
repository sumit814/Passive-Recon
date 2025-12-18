# 🔍 Passive Reconnaissance Framework

A comprehensive Python-based passive reconnaissance framework designed to gather maximum intelligence about targets without direct interaction. This tool aggregates data from 25+ OSINT sources to provide actionable security intelligence.

## ✨ Features

- **🎯 Passive Only**: No direct interaction with target infrastructure
- **📊 Multiple Modules**: 9+ specialized reconnaissance modules
- **🔄 Multi-Source**: Aggregates data from 25+ different sources
- **📈 Output Formats**: Both JSON (for automation) and HTML (for reporting)
- **🎨 Beautiful CLI**: Rich, colorful command-line interface
- **🧹 Data Cleaning**: Automatic deduplication and false positive filtering
- **🔌 Modular Design**: Run individual modules or all at once
- **🔑 API Management**: Centralized API key management

## 🛠️ Modules

| Module | Description | Sources | API Required |
|--------|-------------|---------|--------------|
| **Subdomain Enumeration** | Discover subdomains | crt.sh, SecurityTrails, VirusTotal | Optional |
| **Certificate Search** | SSL/TLS certificate intel | crt.sh, Censys | Optional |
| **Shodan Search** | Internet-exposed assets | Shodan.io | Yes |
| **GitHub Intelligence** | Code & repository search | GitHub API | Yes |
| **Email Harvesting** | Email address discovery | Hunter.io, IntelX | Yes |
| **VirusTotal Lookup** | Domain reputation | VirusTotal | Yes |
| **URLScan Lookup** | Web scanning | URLScan.io | Optional |
| **DNS Intelligence** | DNS records | DNS Resolver | No |
| **WHOIS Lookup** | Registration info | WHOIS | No |

### 🔮 Additional Sources Supported

- **Censys** - Internet-wide scanning
- **ZoomEye** - Cyberspace search engine
- **BinaryEdge** - Internet scanner
- **FOFA** - Cyberspace mapping
- **Netlas** - Internet asset discovery
- **LeakIX** - Leaked data search
- **Onyphe** - Cyber threat intelligence
- **GreyNoise** - Internet noise analysis
- **Vulners** - Vulnerability database
- **PulseDive** - Threat intelligence
- **SecurityTrails** - DNS & SSL history
- **AlienVault OTX** - Open threat exchange
- **WiGLE** - Wireless network mapping
- **IPInfo** - IP intelligence
- **PublicWWW** - Source code search
- **grep.app** - GitHub code search

## 📁 Project Structure

```
passive-recon-framework/
│
├── main.py                    # Main CLI entry point
├── config.py                  # Configuration & API key management
├── requirements.txt           # Python dependencies
├── .env.example              # API keys template
├── README.md                 # This file
│
├── utils/                    # Utility modules
│   ├── __init__.py
│   ├── output_handler.py     # JSON/HTML output generation
│   ├── formatter.py          # Data deduplication & filtering
│   └── visualizer.py         # HTML report generation
│
├── modules/                  # Reconnaissance modules
│   ├── __init__.py
│   ├── base_module.py        # Base class for all modules
│   ├── subdomain_enum.py     # Subdomain enumeration
│   ├── certificate_search.py # SSL certificate search
│   ├── shodan_search.py      # Shodan integration
│   ├── github_intel.py       # GitHub intelligence
│   ├── email_harvesting.py   # Email discovery
│   ├── virustotal_lookup.py  # VirusTotal integration
│   ├── urlscan_lookup.py     # URLScan integration
│   ├── dns_intelligence.py   # DNS enumeration
│   └── whois_lookup.py       # WHOIS lookup
│
├── outputs/                  # Tool-specific output directories
│   ├── subdomain_enumeration/
│   │   ├── data.json
│   │   └── report.html
│   ├── certificate_search/
│   │   ├── data.json
│   │   └── report.html
│   └── ...
│
└── templates/                # HTML report templates (auto-generated)
```

## 🚀 Installation

### Prerequisites

- Python 3.8 or higher
- pip (Python package manager)
- whois command-line tool (for WHOIS module)

### Setup

1. **Clone or download the repository**

```bash
cd /path/to/passive_recon_script
```

2. **Install Python dependencies**

```bash
pip install -r requirements.txt
```

3. **Configure API keys**

```bash
cp .env.example .env
nano .env  # Edit with your API keys
```

4. **Make main script executable** (Linux/Mac)

```bash
chmod +x main.py
```

## 🔑 API Keys Setup

Many modules require API keys. Get free API keys from:

1. **Shodan**: https://account.shodan.io/register
2. **Censys**: https://censys.io/register
3. **GitHub**: https://github.com/settings/tokens
4. **VirusTotal**: https://www.virustotal.com/gui/join-us
5. **Hunter.io**: https://hunter.io/users/sign_up
6. **SecurityTrails**: https://securitytrails.com/app/signup
7. **URLScan**: https://urlscan.io/user/signup
8. **BinaryEdge**: https://app.binaryedge.io/sign-up
9. **ZoomEye**: https://www.zoomeye.org/register
10. **IntelX**: https://intelx.io/signup

Edit `.env` file with your keys:

```bash
SHODAN_API_KEY=your_key_here
GITHUB_TOKEN=your_token_here
VIRUSTOTAL_API_KEY=your_key_here
# ... add more as needed
```

## 💻 Usage

### Basic Commands

**Show help:**
```bash
python main.py --help
```

**List all modules:**
```bash
python main.py modules
```

**Check API key status:**
```bash
python main.py apikeys
```

### Running Scans

**Run all modules against a target:**
```bash
python main.py scan example.com --all
```

**Run a specific module:**
```bash
python main.py scan example.com --module subdomain
```

**Run multiple specific modules:**
```bash
python main.py run example.com --module subdomain
python main.py run example.com --module github
python main.py run example.com --module email
```

**Custom output directory:**
```bash
python main.py scan example.com --all --output /custom/path
```

### Module-Specific Commands

**Subdomain enumeration:**
```bash
python main.py run example.com -m subdomain
```

**Certificate search:**
```bash
python main.py run example.com -m certificate
```

**GitHub intelligence:**
```bash
python main.py run example.com -m github
```

**Email harvesting:**
```bash
python main.py run example.com -m email
```

**Shodan search:**
```bash
python main.py run example.com -m shodan
```

## 📊 Output Format

### JSON Output
Located at: `outputs/<module_name>/data.json`

```json
{
  "metadata": {
    "module": "subdomain_enumeration",
    "target": "example.com",
    "timestamp": "2025-12-16T10:30:00",
    "record_count": 42
  },
  "results": [
    {
      "subdomain": "www.example.com",
      "source": "crt.sh",
      "issuer": "Let's Encrypt"
    }
  ]
}
```

### HTML Output
Located at: `outputs/<module_name>/report.html`

Beautiful, tabular HTML reports with:
- Responsive design
- Color-coded data
- Sortable tables
- Print-friendly layout
- Metadata summary
- Statistics dashboard

## 🎯 Use Cases

1. **Bug Bounty Reconnaissance**
   - Discover subdomains and assets
   - Find exposed services
   - Identify potential attack surfaces

2. **Security Assessments**
   - Asset discovery
   - External perimeter mapping
   - Technology fingerprinting

3. **Threat Intelligence**
   - Monitor brand mentions
   - Track leaked credentials
   - Identify exposed infrastructure

4. **Compliance Auditing**
   - Verify external exposure
   - Document internet-facing assets
   - Certificate monitoring

## 🔒 Security & Ethics

### ⚠️ Important Notes

- **This tool is for AUTHORIZED security research ONLY**
- Only scan targets you have permission to investigate
- Respect API rate limits and terms of service
- Some modules may trigger security alerts (though passive)
- Always follow responsible disclosure practices

### Legal Disclaimer

The developers assume no liability for misuse of this tool. Users are responsible for complying with all applicable laws and regulations.

## 🛡️ Features in Detail

### Data Deduplication
- Automatic removal of duplicate entries
- Hash-based comparison
- Configurable deduplication keys

### False Positive Filtering
- Pattern-based filtering for subdomains
- Email validation
- Private IP filtering
- URL validation

### Rate Limiting
- Automatic retry with exponential backoff
- Respect for API rate limits
- Configurable timeout settings

### Error Handling
- Graceful failure handling
- Detailed error messages
- Continue-on-error for batch operations

## 🔧 Advanced Usage

### Creating Custom Modules

1. Create a new file in `modules/` directory
2. Extend `BaseModule` class
3. Implement required methods:
   - `collect()` - Data collection logic
   - `get_api_endpoint()` - API endpoint
   - `requires_api_key()` - API requirement flag

Example:

```python
from modules.base_module import BaseModule

class CustomModule(BaseModule):
    def __init__(self):
        super().__init__("custom_module")
    
    def get_api_endpoint(self):
        return "https://api.example.com"
    
    def requires_api_key(self):
        return True
    
    def collect(self, target, **kwargs):
        # Your collection logic
        return []
```

### Extending Output Formats

Modify `utils/visualizer.py` to customize HTML reports or add new formats.

## 📈 Roadmap

- [ ] Add more data sources (Rapid7, Spyse, etc.)
- [ ] Implement caching to avoid redundant API calls
- [ ] Add export to CSV and PDF formats
- [ ] Create web dashboard for results
- [ ] Add diff/compare functionality for monitoring
- [ ] Implement parallel processing for faster scans
- [ ] Add Telegram/Slack notifications
- [ ] Create Docker container
- [ ] Add automated scheduling

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Add your module or enhancement
4. Test thoroughly
5. Submit a pull request

## 📝 Changelog

### v1.0 (2025-12-16)
- Initial release
- 9 core modules implemented
- 25+ data sources integrated
- JSON and HTML output formats
- Beautiful CLI interface
- Comprehensive error handling

## 📄 License

This project is provided as-is for educational and authorized security research purposes.

## 🙏 Credits

- Built with: Python, Rich, Click, Requests, BeautifulSoup
- Inspired by: Recon-ng, theHarvester, Amass
- Data sources: All the amazing OSINT platforms listed above

## 📧 Support

For issues, questions, or contributions, please open an issue on the repository.

---

**⚡ Happy (Passive) Hunting! ⚡**

Made with ❤️ for the security community
