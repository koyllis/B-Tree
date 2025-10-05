# B-Tree Plus Engine

![B-Tree Plus Engine](btree.png)

---

## 🧩 Overview

The B-Tree Plus Engine is a high-performance, open-source NoSQL engine written in C#.
It provides record-level access with full control, minimal dependencies, and exceptional speed.
Inspired by the classic Btrieve architecture, it combines simplicity, durability, and modern design.

---

## ⚙️ Features

- Lean NoSQL Engine: Built for direct record access — no ORM, no SQL parser, zero overhead.
- File-Based Storage: Persistent data files with optional in-memory tables for ultra-fast operations.
- Structured Records: Named fields such as `code`, `desc`, `price`, supporting both fixed and variable lengths.
- Manager → Btrieve API: Clean high-level access pattern for inserts, finds, deletes, and updates.
- Always 99% Full Pages: Maximizes density and minimizes I/O.
- Sharding & Secondary Indexes: Built-in support for distributed and multi-index workloads.
- Crash-Proof Integrity: Zero-crash architecture — every write path and index update is fail-safe.
- Audit Logging: Persistent `trans.bin` file records all activity for full traceability.
- Attachments: Records can include embedded files stored within a file (`item.data`).
- Apache 2.0 License: Open source and free for both commercial and private projects.

---

## 🚀 Getting Started

```csharp
using Btrieve;

Manager man = Manager.DefaultManager;
Btrieve bt = man.Create("pos", "item");

bt.SetString("code", "Test");
bt.SetString("desc", "Demo Item");
bt.Insert();

Console.WriteLine("Inserted one record into pos/item table.");
```

---

## 📦 Dependencies

- **iText 7** – Used for PDF generation and document handling.
  Install from NuGet:
  ```bash
  dotnet add package itext7
  ```
- **.NET Runtime 6 or later** – required to build and run the engine.
- No other external dependencies — the engine is fully self-contained.

---

## 🏗️ Build

```bash
cd /home/mmh/standard/Btrieve
dotnet build
```

Requires .NET 6 or later.

---

## 📂 Folder Layout

```
standard/Btrieve/
 ├── Btrieve.csproj
 ├── Manager.cs
 ├── Btrieve.cs
 ├── BPlusTreeInMemory.cs
 └── README.md
```

---

## 🗺️ Roadmap

- [ ] File-backed page store
- [ ] Node split / merge logic
- [ ] Enhanced transaction system
- [ ] Range iterators and cursors
- [ ] Bulk-load and rebuild tools
- [ ] Integrated benchmarks

---

## ❓ Technical Highlights & FAQ

- Purpose: A lean, mean, ultra-fast NoSQL engine for direct record access and embedded use.
- Usage Scope: Can be embedded anywhere — POS, ERP, or standalone systems.
- Storage Model: Primarily file-based for persistence, with optional in-memory tables for speed.
- Design Philosophy: Full control, minimal dependencies, no async, deterministic behavior.
- Performance Focus: Optimized for everything — speed, memory, concurrency, and stable latency.
- Data Model: Structured records with named fields (e.g. `code`, `desc`, `price`), supporting both fixed and variable-length formats.
- Access Pattern: All interaction flows through the Manager → Btrieve layer for safety and consistency.
- Unique Edge: Always maintains 99% full pages, supports sharding, and has secondary indexes built-in.
- Table Layout: Each table consists of `item` (raw records), `item.k` (index file), and `item.data` — a container holding attachments (files within a file, linked to specific records).
- Reliability: Zero-crash architecture — every write path is designed for full integrity and recoverability.
- Audit Trail: Maintains a persistent `trans.bin` file logging all operations for auditing and verification.
- Intended Use: Suitable both as a low-level developer component and as a self-contained embedded database engine.

---

## 📜 License

Apache 2.0 © 2025 koyllis
