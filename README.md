<div align="center">
▶️ India Trending Pulse · YouTube Trending Videos (2023 – 24)
What it takes to hit YouTube's Trending list in India: categories, views vs likes, and how fast videos trend

</div>

Speed is everything on YouTube India. 89% of trending videos hit the list within a day of upload, and most stay only 2–3 days. Entertainment fills 46% of the list and TV networks lead the channel chart, while gaming and comedy creators earn the most likes per view. The single most-viewed trending video was GTA VI Trailer 1 (145M views).

<div align="center">
🎬 Trending Videos	📺 Channels	👁️ Median Views	👍 Like Rate	⚡ Trended in ≤ 1 Day	🌍 Total Views
27,775	2,570	704,604	3.63%	89%	51.9 B
</div>

Page 1 · What Trends in India

What Trends in India

Page 2 · Views, Likes & Speed

Views, Likes & Speed

🎯 Questions This Dashboard Answers
🗂️ Which categories dominate India's Trending list?
📺 Which channels trend the most?
👁️ How do views relate to likes? Do bigger hits get more engagement?
⏱️ How fast do videos reach Trending, and how long do they stay?
🕘 What is the best day and hour to upload?
📂 Data Source
	
Dataset	YouTube Trending Video Dataset (updated daily) by Rishav Sharma, Kaggle (India file)
Collected via	YouTube Data API (daily snapshots of the India Trending list)
Full file	251,277 daily trending entries · 78,847 videos · 12 Aug 2020 – 15 Apr 2024
Used here	27,775 videos that first trended 1 Jan 2023 – 15 Apr 2024 (the most recent data available)

ℹ️ Why it stops in 2024: the Kaggle dataset's last update was 15 Apr 2024, and YouTube retired its public Trending page on 1 July 2025.

🧹 Data Preparation
Step	Why
📅 Collapsed 251K daily entries to one row per video	Each video appears once per day it trended
📈 Kept peak views, likes and comments	Stats keep growing while a video trends
⏱️ Calculated days to trend (upload → first trending day)	"How fast" metric
📆 Calculated days on trending	"How long" metric
🕘 Converted upload time UTC → IST	Correct best-time-to-upload analysis
🚫 Left out dislikes	YouTube stopped publishing dislike counts in 2021
🔒 Blanked likes and comments where the creator turned them off	So zeros don't distort engagement
🗃️ Moved categories and channels into lookup tables	Smaller file; a cleaner, linked model

📐 Key DAX Measures
DAX
Trending Videos     = COUNTROWS ( Videos )

Median Views        = MEDIAN ( Videos[Views] )

-- Views-weighted like rate (ignores videos whose likes are hidden)
Like Rate %         = DIVIDE ( SUM ( Videos[Likes] ),
                               CALCULATE ( SUM ( Videos[Views] ), NOT ISBLANK ( Videos[Likes] ) ) )

Same or Next Day %  = DIVIDE ( CALCULATE ( COUNTROWS ( Videos ), Videos[Days to Trend] <= 1 ),
                               [Trending Videos] )

Avg Days on Trending = AVERAGE ( Videos[Days on Trending] )

Share of Trending   = DIVIDE ( [Trending Videos], CALCULATE ( [Trending Videos], ALLSELECTED ( Videos ) ) )

🏆 The "Top 10 channels" chart uses Power BI's built-in Top N visual filter, so it stays fast and responds to every slicer.

📊 Dashboard Walkthrough

🎛️ Filters on both pages (synced): Year · Month · Category · Time to Trend

📈 Page 1 · What Trends in India
Visual	What it shows
5 KPI cards	Trending videos · channels · median views · like rate · % trended within a day
Category bar	Which categories trend most
Monthly column	New videos entering Trending each month
Upload heatmap	Trending videos by upload day × hour (IST)
Top channels	Top 10 channels by number of trending videos
⚡ Page 2 · Views, Likes & Speed
Visual	What it shows
Views vs likes scatter	Each category's median views vs like rate (bubble = video count)
Like rate by view range	Do bigger hits get more likes per view?
Time to trend	Days from upload to Trending
Trending duration	How many days videos stay trending
Top videos table	Title, channel, category, views, like rate, speed, duration and a ▶️ watch link
💡 Key Insights
1️⃣ The biggest trending videos
#	Video	Channel	Views*
🥇	Grand Theft Auto VI Trailer 1	Rockstar Games	145.1 M
🥈	Salaar Teaser	Hombale Films	118.2 M
🥉	Pushpa 2 The Rule Teaser	Mythri Movie Makers	112.5 M
4	Face Your Biggest Fear To Win $800,000	MrBeast	109.8 M
5	Kya Loge Tum (Akshay Kumar)	DM - Desi Melodies	106.5 M

<sub>*Highest view count recorded while the video was on India's Trending list.</sub>

🎮 GTA VI Trailer 1 was also the most-liked trending video (10.8 M likes)
🎥 MrBeast has 5 of the top 10 most-viewed trending videos, the only creator in the top 10 who isn't a film studio or music label
🎞️ South Indian cinema rules the trailer race: Salaar and Pushpa 2 teasers each passed 110 M views
💬 Most-commented: Sidhu Moose Wala, "Mera Na" with 1.25 M comments
🏏 Top sports video: Asia Cup 2023 Final, India vs Sri Lanka highlights (32 M)
2️⃣ Entertainment and TV networks dominate
🎭 Entertainment = 46% of all trending videos, then People & Blogs 16%, Music 9% and Gaming 6%
📺 Top channels are TV networks: Vijay Television (943), Sun TV (749), Sony SAB (547)
🚶 Sourav Joshi Vlogs (468) is the top individual creator
🔟 The top 10 channels account for 18% of all trending videos
3️⃣ Speed is everything
⚡ 89% of videos reach Trending the same or next day after upload
⏳ They don't stay long: an average of 3 days, and only ~1% last 8+ days
🏆 The longest-trending videos (11 days): LEO: Bloody Sweet Promo and KALAASTAR (Honey 3.0)
4️⃣ Views ≠ engagement
👍 Gaming (6.2%), Comedy (6.1%) and People & Blogs (5.9%) get the most likes per view
📰 News & Politics (1.7%) and Film & Animation (2.0%) get the fewest
📉 The biggest hits (20M+ views) average a 3.1% like rate vs 4.3% for smaller videos (<250K)
5️⃣ When to upload
🕘 Peak upload hours for trending videos: 9 PM, 7 PM, 11 AM and 6 PM IST
📅 Thursday and Friday produce the most trending videos; Saturday the fewest
🔥 Single best slots: Sunday 10 AM and Monday 9 PM
⚠️ Limitations
Data ends 15 Apr 2024 (April 2024 is a partial month)
Days to trend is measured in whole days: the dataset records only the date a video trended, not the time
Views and likes are peak values while trending, not today's totals
Trending measured YouTube's editorial + algorithmic list, not simply the most-viewed videos
📚 What I Learned
🔁 Pick the right level of detail: daily snapshots double-count videos, so collapsing to one row per video was essential
🕘 Time zones matter: converting UTC to IST changed the "best time to upload" completely
⚖️ Weighted vs simple averages: a views-weighted like rate stops tiny videos from skewing engagement
🧱 Power Query for derived columns keeps the source file small and the logic transparent
🗂️ Lookup tables cut the model size and made category and channel filtering clean

▶️ How to Use
Clone the repo
bash
git clone https://github.com/<your-username>/YouTube-India-Trending-Dashboard.git
Open YouTube_India_Trending_Dashboard.pbix (or the .pbit) in Power BI Desktop
Explore: filter by year, month, category or speed, click any bar or heatmap cell to cross-filter, and click ▶️ in the table to watch a video
🙏 Credits
Data: YouTube Trending Video Dataset by Rishav Sharma (Kaggle, collected via the YouTube Data API)
YouTube is a trademark of Google LLC. This is an independent analysis project.
<div align="center">
👋 Built by Niranjan Bhat

One data project a day,
