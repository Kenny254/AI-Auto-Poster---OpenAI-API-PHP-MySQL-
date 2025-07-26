# 📰 AI News Auto-Poster with OpenAI API (PHP + MySQL)

## 👋 Hello and Welcome!

Hey there! 👋  
Thanks for visiting this project. I built it to help fellow developers, content creators, and AI enthusiasts like you automate the generation and publishing of news articles using OpenAI’s API. This script fetches fresh, Kenya-relevant news articles in categories like Technology, Politics, Medicine, Education, Business, and Entertainment — and inserts them straight into your database.

No more writing boilerplate news manually. The script generates AI-powered content, checks for duplicates, and logs what it inserted — all in a cron-job-friendly format. Whether you’re running a blog, a content site, or building a news aggregator, this should save you serious time.

---

## 🚀 How It Works

1. The PHP script loops through your selected news categories.
2. For each category, it calls OpenAI’s GPT model with a writing prompt.
3. It receives and parses 3 articles (each with a title and body).
4. It checks the database for duplicates (by title).
5. It inserts only fresh articles into the `gonews` table.
6. Logs are saved in `cron_news.log` to track each run.

---

## ⚙️ Configuration

Before running the script:

1. Replace the following placeholders in the script:
   - `DB_USERNAME`, `DB_PASSWORD`, `DB_NAME` – your MySQL DB config
   - `YOUR_OPENAI_API_KEY` – your OpenAI API key

2. Ensure the following MySQL table exists:

```sql
CREATE TABLE `gonews` (
  `id` INT(11) NOT NULL AUTO_INCREMENT PRIMARY KEY,
  `category` VARCHAR(32) NOT NULL,
  `title` VARCHAR(255) NOT NULL,
  `slug` VARCHAR(255) NOT NULL,
  `content` TEXT NOT NULL,
  `author_id` INT(11) DEFAULT NULL,
  `featured_image` VARCHAR(255) DEFAULT NULL,
  `is_top` TINYINT(1) DEFAULT 0,
  `status` ENUM('draft','published','archived') DEFAULT 'draft',
  `created_at` DATETIME DEFAULT CURRENT_TIMESTAMP,
  `updated_at` DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=latin1 COLLATE=latin1_swedish_ci;

🙏 Thanks
I truly appreciate you taking a look at this project! I hope it helps you build something amazing. If you have ideas, need improvements, or want to collaborate, feel free to fork, star ⭐️, or contribute. Let AI take care of the writing so you can focus on building. Happy coding! 🚀
