# AS-Prefix Data

🌍 This dataset contains routing prefix information associated with Autonomous Systems.

## Summary

- ✅ Total ASNs retrieved: 118523
- 📡 ASNs with active prefixes: 83853
- 📁 Files generated: 83853

Files are stored in the "data" subdirectory:
```

data/AS1234
data/AS5678
...
```


Each file contains:
- 🏷️  Header with ASN and name
- 🌐 One IP prefix per line

Data was compiled from publicly available routing information using automated tools.

> 🕒 Last updated: 2026-03-01 16:06:58 UTC

## ⚠️ Disclaimer

This data is provided for informational and research purposes only. The accuracy, completeness, and timeliness of the information are not guaranteed. Network routing data is dynamic and may change frequently;
this dataset reflects a snapshot in time and may not represent current routing states. The authors and maintainers do not assume any liability for errors, omissions, or damages arising from the use of this information.
It is the user's responsibility to verify critical data through authoritative sources such as RIPE, APNIC, or RouteViews.

## 🛠️ Usage Instructions

### 1. 📂 Explore Data by ASN

Each ASN has a corresponding file in the `data/` directory named in the format `ASXXXX`. The first line is the ASN, followed by one prefix per line.

### 2. 💻 Read Prefixes Programmatically

The format is plain text, making it easy to parse in any programming language. For example, in Go:

```go

package main

import (
    "bufio"
    "fmt"
    "os"
)

func main() {
    file, err := os.Open("data/AS1234")
    if err != nil {
        panic(err)
    }
    defer file.Close()

    scanner := bufio.NewScanner(file)
    for scanner.Scan() {
        prefix := scanner.Text()
        fmt.Println("Prefix:", prefix)
    }
}
```


### 3. 📊 Batch Processing

Use shell commands to process multiple files. For example, count total prefixes:

```sh

find data/ -type f -name "AS*" -exec cat {} \; | wc -l
```


Or list all prefixes from a specific ASN range:

```sh

grep -E "^(198|199)\." data/AS* | cut -d: -f2
```


### 4. 🔗 Integration with Network Tools

You can import prefix lists into:
- 🔥 Firewalls (e.g., iptables, nftables)
- 🔄 Routing daemons (e.g., BIRD3, FRR)
- 🛡️  Security tools (e.g., for DDoS source identification)

### 5. ✅ Validation and Enrichment

To ensure reliability, cross-check prefixes with real-time BGP data from:
- 🌐 RIPE RIS (https://ris.ripe.net)
- 🌐 RouteViews (https://www.routeviews.org)
- 🌐 PeeringDB (https://peeringdb.com)

🔐 Always respect data usage policies and applicable laws when applying this information in production environments.
