#Python Asynchronous BitTorrent Client

An experimental, fully-asynchronous BitTorrent client written from scratch in Python 3. 

This project was built to explore and implement the BitTorrent protocol (specifically the Bencoding format, tracker communication, and peer-to-peer message flow) leveraging modern Python features such as `asyncio` and static type hinting.

## Features
- **Asynchronous Architecture:** Built using `asyncio` for non-blocking network operations and concurrency.
- **Bencoding Implementation:** Custom encoders and decoders for parsing `.torrent` files and BitTorrent messages.
- **Tracker Communication:** Connects to HTTP/UDP trackers to retrieve active peer lists.
- **Peer-to-Peer Protocol:** Establishes concurrent connections with remote peers.
- **Streaming Decoders:** Uses Python async iterators to continuously stream and decode binary data from raw sockets into standard message objects.
- **Piece Management:** Manages downloaded pieces and handles the assembly of the target file.

## Getting Started

### Prerequisites
- Python 3.5+
- (Optional) `make` for running utility scripts

### Installation
Clone the repository and install the required dependencies:

```bash
git clone https://github.com/app1o/BitTorrentCLient.git
cd BitTorrentCLient
make init
```

### Running the Client

To download a torrent, simply run the client and pass the path to your `.torrent` file:

```bash
python pieces.py -v path/to/your/file.torrent
```

For example, using the provided test torrent:

```bash
python pieces.py -v tests/data/bootfloppy-utils.img.torrent
```

*Note: The client can be stopped gracefully at any time using `Ctrl + C`.*

### Running Tests

To run the unit test suite:

```bash
make test
```

## Architecture

The project is structured around several key components:

- **`TorrentClient`**: The central controller that coordinates tracker communication, peer queuing, and shutdown sequences.
- **`PieceManager`**: Handles the logic for requesting pieces and reassembling the downloaded file in memory.
- **`protocol.py`**: Manages the peer connections, control flow, and message passing.
- **`bencoding.py`**: A robust implementation of the BitTorrent Bencoding specification.

## Disclaimer

This client is currently experimental and primarily built for educational purposes. It focuses on downloading (leeching) and currently lacks advanced features like seeding, resuming partial downloads, or advanced piece-selection algorithms (e.g., rarest-first). 

---
*Created for educational exploration of asynchronous programming and P2P networks.*
