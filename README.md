# Hit FM 年度百首單曲查詢小助手
純靜態網站：28年、2,800筆年度榜單。搜尋／統計／推薦在瀏覽器執行；自然語言透過使用者自己的Groq金鑰，只呼叫一次模型產生白名單查詢條件。

## 放上 GitHub Pages
1. 建立 GitHub repository，將解壓縮後的 `index.html` 和 `assets` 資料夾上傳至 repository 根目錄（不要再包一層資料夾）。
2. Settings → Pages → Deploy from a branch，選 main / root，儲存。
3. 等待Pages發布完成後開啟網址。請透過HTTP網站開啟，直接雙擊本機HTML會因瀏覽器檔案限制讀不到JSON。
也可以用 `python -m http.server 8000` 在本機預覽。

## AI功能
點「AI連線設定」貼上自己的Groq API key。key只在頁面記憶體，不會寫入原始碼、localStorage、sessionStorage或網址；重整後清除。請只在自己信任的網站版本輸入key。請求直接送至 `https://api.groq.com/openai/v1/chat/completions`，額度屬於所輸入key的帳號。沒有key仍能使用全部直接查詢，以及有限的規則式問句。沒有內建共享key或免費AI服務。
模型：openai/gpt-oss-120b。只有問題與上一輪查詢條件送到Groq，不會送出整份榜單；無第二次模型文字生成。真實API需要使用者自己的金鑰，未宣稱已完成帶金鑰的端到端測試。

## 功能
- 年份榜單、歌手（含部分別名）、歌曲／專輯條件查詢
- 歌手比較、逐年統計、年度冠軍與並列名次
- 依條件隨機推薦、相近榜單年代推薦（非聲音／情緒分析）
- CSV匯出、逐首YouTube搜尋連結（不是建立YouTube歌單）
- 語句與AI解析不能保證正確，可展開查詢條件核對

上榜紀錄不等於不同作品數；合唱每位署名各計一次，團體不拆成員。別名與署名規則仍有局限。資料範圍1998–2025，2026尚未收錄；榜單年份不一定是發行年份。

資料來源：Hit FM 官方歷年年度百首單曲。此為個人非官方專案。
