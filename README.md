Docker Compose for ZNY support enabled MPOS
===========================================

**Note!** This docker-compose does **not** include `bitzenyd` (or something coin daemon) container. Please install it by yourself beforehand.

Installation
------------
1. `cp .env.production.sample .env.production`
2. Edit `.env.production` to make it fits to your environment
3. Edit `mpos/config/*.inc.php` (especially `mpos/config/global.inc.php`) if needed.
4. Edit `stratum-mining/conf/config.py` if needed.
5. `docker-compose build && docker-compose up`

Donation
--------

- **BTC**: `1NP1LCSp8Q6YZLNSkzWAj4XmC8aJvzPJpv`
- **ZNY**: `ZrcXs55d6PCYmy2Kyh2AK24HKuXo833U6f`
