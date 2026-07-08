# Chat Analytics on MongoDB

A runnable Colab notebook that proves MongoDB can serve chat analytics without a separate data warehouse. It generates 2,000 synthetic support conversations, loads them into your MongoDB, and answers ten real analytics questions with aggregation pipelines and charts — then showcases Vector Search, Atlas Search, change streams, and time-series collections.

**Notebook:** [`chat_analytics_mongodb.ipynb`](chat_analytics_mongodb.ipynb)

**▶ [Open in Colab](https://colab.research.google.com/github/munish-mongodb/chat-analytics-mongodb/blob/main/chat_analytics_mongodb.ipynb)**

Open it in Colab, paste a MongoDB connection string when prompted, and run top to bottom. The data is generated in-cell, so nothing else is needed.

## Get a MongoDB connection string (Atlas free tier)

The notebook works against any MongoDB 6.0+. The easiest way to get one is a free Atlas M0 cluster:

1. Sign up at [cloud.mongodb.com](https://cloud.mongodb.com) and create a project.
2. **Create a cluster** → choose **M0 (free)**, pick any cloud provider/region, create it. Provisioning takes a couple of minutes.
3. **Database Access** → *Add New Database User*. Set a username and password (auth method: password). Give it *Read and write to any database*.
4. **Network Access** → *Add IP Address*. Colab runs from rotating IPs, so add `0.0.0.0/0` (allow access from anywhere). Fine for a throwaway demo cluster; tighten or delete it afterward.
5. **Connect** → *Drivers* → *Python* → copy the connection string. It looks like:
   ```
   mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/?retryWrites=true&w=majority
   ```
   Replace `<username>` and `<password>` with the user you created in step 3.
6. Paste that string into the notebook's `getpass` prompt. The notebook creates and uses a database called `chat_demo` automatically.

The connection string is read via `getpass`, so it never appears in the notebook or its saved output. Do not paste it into a cell.
