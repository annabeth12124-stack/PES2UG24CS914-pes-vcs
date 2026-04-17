# PES Version Control System (PES-VCS)

## 📌 Overview

This project implements a simplified version control system inspired by Git. It supports core version control functionalities such as object storage, indexing, tree construction, commits, and history traversal.

The system demonstrates how Git internally manages data using content-addressable storage, trees, and commit graphs.

---

## 🚀 Features

### ✅ Phase 1: Object Storage

* Implements blob storage using SHA-256 hashing
* Deduplication of identical objects
* Object storage in `.pes/objects/` using sharded directories
* Functions:

  * `object_write`
  * `object_read`

---

### ✅ Phase 2: Tree Objects

* Builds directory tree snapshots from index
* Deterministic serialization of tree structures
* Supports parsing and reconstruction of trees
* Functions:

  * `tree_from_index`
  * `tree_serialize`
  * `tree_parse`

---

### ✅ Phase 3: Index and Commit

* Implements staging area (`.pes/index`)
* Supports:

  * `pes add`
  * `pes status`
* Commit creation with:

  * tree reference
  * author metadata
  * message
* Updates HEAD reference

---

### ✅ Phase 4: Commit History and Log

* Parent-based commit chaining
* Traverses commit history like a linked list
* Implements:

  * `pes log`
* Displays:

  * commit hash
  * author
  * timestamp
  * message

---

## 🧠 Core Concepts Implemented

| Concept      | Description                 |
| ------------ | --------------------------- |
| Blob         | File content stored as hash |
| Tree         | Directory snapshot          |
| Index        | Staging area                |
| Commit       | Snapshot + metadata         |
| HEAD         | Current branch reference    |
| Object Store | Content-addressable storage |

---

## 📂 Project Structure

```
.pes/
├── objects/        # Stored objects (blobs, trees, commits)
├── refs/
│   └── heads/      # Branch references
├── HEAD            # Current branch pointer
├── index           # Staging area
```

---

## ⚙️ Build Instructions

```bash
make clean
make all
```

---

## ▶️ Usage

### Initialize repository

```bash
./pes init
```

### Add files

```bash
./pes add <file>
```

### Check status

```bash
./pes status
```

### Commit changes

```bash
./pes commit -m "message"
```

### View commit history

```bash
./pes log
```

---

## 🧪 Example Workflow

```bash
./pes init

echo "Hello" > hello.txt
./pes add hello.txt
./pes commit -m "Initial commit"

echo "World" >> hello.txt
./pes add hello.txt
./pes commit -m "Update file"

./pes log
```

---

## 📸 Screenshots Included

* Object storage structure (`find .pes/objects`)
* Tree serialization output
* Index file contents
* Status output
* Commit history (`pes log`)

---

## 🧩 Implementation Highlights

* SHA-256 based object storage
* Content-addressable design
* Tree and commit graph construction
* Safe commit traversal using parent links
* Detection of uncommitted changes

---

## ⚠️ Limitations

* No merge or branching support (beyond basic HEAD)
* No remote repository integration
* No conflict resolution

---

## 🧠 Learning Outcomes

* Understanding of Git internals
* File system-level version control design
* Hash-based storage systems
* Commit graph traversal

---

## 👩‍💻 Author

**Sakshi Srinivas Ghodke**

---

## 📌 Conclusion

This project successfully replicates the core mechanisms of Git, including object storage, indexing, tree construction, and commit history traversal, providing a strong foundation for understanding modern version control systems.

---
