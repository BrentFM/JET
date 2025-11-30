# JET — JSON Efficient Tokenizer

> **Transform JSON into token-efficient, LLM-friendly formats**

JET is an intelligent JSON encoder that reduces token usage by up to 60% while maintaining perfect readability for Large Language Models. It automatically analyzes your JSON structure and selects the most efficient encoding strategy for each part of your data.

## 🎯 What is JET?

JET (JSON Efficient Tokenizer) is a universal encoder that takes any valid JSON and outputs a significantly more token-efficient representation. Unlike simple minification, JET uses multiple encoding strategies to intelligently compress your data while keeping it easy for LLMs to parse.

### Key Features

- ✅ **Universal**: Accepts any valid JSON structure
- ✅ **Intelligent**: Automatically selects optimal encoding strategies
- ✅ **Token-Efficient**: Reduces tokens by 40-60% compared to standard JSON
- ✅ **LLM-Friendly**: Designed for easy parsing by language models
- ✅ **Lossless**: Perfect round-trip conversion
- ✅ **Deterministic**: Same input always produces same output

## 🚀 Try It Now

**👉 [Use JET on brenthaskins.com/tools/jet](https://brenthaskins.com/tools/jet)**

Try it with your own JSON or use the examples provided. See real-time token savings and encoding statistics!

## 📊 Encoding Strategies

JET uses multiple encoding strategies, automatically selecting the best one for each part of your JSON:

### 1. **YAML-Like Encoding**
For objects and nested structures, JET uses YAML-style indentation:
```
context:
  task: Our favorite hikes together
  location: Boulder
  season: spring_2025
```

### 2. **TOON Blocks (Table Format)**
For uniform arrays of objects, JET uses a compact table format:
```
users[3]{id,name,email,age}:
  1,Alice,alice@example.com,30
  2,Bob,bob@example.com,25
  3,Charlie,charlie@example.com,35
```

### 3. **Compact Array Notation**
For simple arrays of primitives:
```
friends[3]: ana,luis,sam
```

### 4. **Key Aliasing**
For frequently repeated long keys, JET creates short aliases:
```
@a: "user_id"  // alias definition
users[2]{@a,name}:
  123,Alice
  456,Bob
```

### 5. **Smart Strategy Selection**
JET analyzes your JSON structure and automatically:
- Detects uniform arrays → uses TOON blocks
- Identifies repeated keys → creates aliases
- Finds nested structures → uses YAML-like formatting
- Handles mixed data → combines strategies optimally

## 💡 Example

**Input (Standard JSON):**
```json
{
  "users": [
    {"id": 1, "name": "Alice", "email": "alice@example.com", "age": 30},
    {"id": 2, "name": "Bob", "email": "bob@example.com", "age": 25},
    {"id": 3, "name": "Charlie", "email": "charlie@example.com", "age": 35}
  ],
  "metadata": {
    "totalUsers": 3,
    "lastUpdated": "2025-01-28"
  }
}
```

**Output (JET Encoded):**
```
users[3]{id,name,email,age}:
  1,Alice,alice@example.com,30
  2,Bob,bob@example.com,25
  3,Charlie,charlie@example.com,35
metadata:
  totalUsers: 3
  lastUpdated: 2025-01-28
```

**Token Savings:** ~60% reduction (from ~45 tokens to ~18 tokens)

## 🔌 API Access

JET is available as a REST API for integration into your applications. The API includes:

- **Rate Limiting**: Prevents abuse with per-key/IP limits
- **API Key Authentication**: Optional authentication for production use
- **CORS Enabled**: Works from any origin
- **Real-time Encoding**: Fast, efficient processing

**👉 Get API access and documentation at [brenthaskins.com/tools/jet](https://brenthaskins.com/tools/jet)**

Click the "API" button in the tool interface to view:
- API endpoint details
- Request/response examples
- cURL and JavaScript code samples
- Rate limit information

## 🎨 Use Cases

- **LLM Context Optimization**: Reduce token usage in prompts
- **API Response Compression**: Send more data with fewer tokens
- **Cost Reduction**: Lower API costs for LLM services
- **Data Transfer**: Efficient JSON serialization
- **Prompt Engineering**: Maximize context window utilization

## 📈 Performance

- **Speed**: Processes JSON in milliseconds
- **Efficiency**: 40-60% token reduction on average
- **Scalability**: Handles large JSON structures (up to 5MB)
- **Memory**: Efficient in-memory processing

## 🔒 Security & Privacy

- **No Data Storage**: All processing happens in-memory
- **No External Services**: Self-contained encoding
- **Rate Limited**: Built-in protection against abuse
- **CORS Configured**: Secure cross-origin access

## 🛠️ Technical Details

### Supported Input
- Any valid JSON (objects, arrays, primitives)
- Nested structures of any depth
- Mixed data types
- Large payloads (up to 5MB)

### Output Format
- Deterministic encoding
- Human-readable
- LLM-parseable
- Strategy metadata included

### Encoding Process
1. **Parse**: Convert JSON to internal AST
2. **Analyze**: Compute structure statistics
3. **Optimize**: Build alias dictionary
4. **Encode**: Apply optimal strategies recursively
5. **Output**: Generate final encoded text

## 📚 Learn More

- **Try the Tool**: [brenthaskins.com/tools/jet](https://brenthaskins.com/tools/jet)
- **View Blog Post**: Learn about the design decisions and strategies
- **API Documentation**: Available in the tool interface

## 🤝 Contributing

This is a showcase project. For questions, feedback, or suggestions, visit the tool page and use the contact options available there.

## 📄 License

This project is for demonstration purposes. See the tool page for usage terms.

---

**Built by [Brent Haskins](https://brenthaskins.com)** | [Portfolio](https://brenthaskins.com) | [Tools](https://brenthaskins.com/tools)
