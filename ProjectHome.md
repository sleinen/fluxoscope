This project contains code to process Cisco NetFlow(TM) accounting records, as can be sent from various brands and types of routers.  It aggregates the accounting records by (customer) site, external AS, and heuristically guessed application protocol.  Aggregated counter matrices are periodically written to text files.  From there, they can be further processed into RRD files for graphical representation.

Fluxoscope has been used for volume-based billing at SWITCH, the Swiss education and research network, since 1999.