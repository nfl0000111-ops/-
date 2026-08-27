<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>半蔵門駅前整体院 - ご来店アンケート</title>
  <style>
    body { font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', sans-serif; background: #f4f7f9; padding: 15px; margin: 0; color: #2c3e50; }
    .card { background: white; padding: 24px; border-radius: 12px; max-width: 480px; margin: 10px auto; box-shadow: 0 4px 12px rgba(0,0,0,0.08); }
    .header { text-align: center; border-bottom: 2px solid #00c6ff; padding-bottom: 12px; margin-bottom: 16px; }
    h1 { font-size: 1.3rem; margin: 0; color: #1e3c72; }
    .subtitle { font-size: 0.85rem; color: #64748b; margin-top: 4px; }
    .section-title { font-weight: bold; margin-top: 18px; font-size: 0.95rem; display: flex; align-items: center; }
    .req { background-color: #ef4444; color: white; font-size: 0.7rem; padding: 1px 5px; border-radius: 3px; margin-left: 6px; }
    .tag-group { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 8px; }
    .tag { background: #f1f5f9; border: 1px solid #cbd5e1; padding: 8px 12px; border-radius: 20px; font-size: 0.85rem; cursor: pointer; user-select: none; color: #475569; transition: all 0.2s; }
    .tag.active { background: #0284c7; color: white; border-color: #0284c7; font-weight: bold; }
    button.btn-submit { width: 100%; background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%); color: white; border: none; padding: 14px; border-radius: 8px; font-weight: bold; margin-top: 22px; font-size: 1rem; cursor: pointer; }
    .result-box { margin-top: 20px; padding: 16px; background: #f0fdf4; border: 1px solid #bbf7d0; border-radius: 8px; display: none; }
    .btn-copy { background: #16a34a; color: white; border: none; padding: 12px; width: 100%; border-radius: 6px; margin-top: 12px; font-weight: bold; cursor: pointer; font-size: 0.95rem; }
  </style>
</head>
<body>

<div class="card">
  <div class="header">
    <h1>半蔵門駅前整体院</h1>
    <div class="subtitle">ご来店・施術に関するアンケート</div>
  </div>

  <div class="section-title">1. 本日受けられた施術・お悩み <span class="req">必須</span></div>
  <div class="tag-group" id="menu-group">
    <div class="tag" onclick="toggleTag(this)">腰痛・骨盤矯正</div>
    <div class="tag" onclick="toggleTag(this)">首肩こり・頭痛</div>
    <div class="tag" onclick="toggleTag(this)">猫背・姿勢改善</div>
    <div class="tag" onclick="toggleTag(this)">産後骨盤矯正</div>
    <div class="tag" onclick="toggleTag(this)">小顔・美容整体</div>
  </div>

  <div class="section-title">2. 当院の良かった点・印象</div>
  <div class="tag-group" id="feature-group">
    <div class="tag" onclick="toggleTag(this)">丁寧なカウンセリング</div>
    <div class="tag" onclick="toggleTag(this)">説明が分かりやすい</div>
    <div class="tag" onclick="toggleTag(this)">駅近で通いやすい</div>
    <div class="tag" onclick="toggleTag(this)">院内が清潔で安心</div>
  </div>

  <div class="section-title">3. 施術後の変化・感想</div>
  <div class="tag-group" id="impression-group">
    <div class="tag" onclick="toggleTag(this)">体がとても軽くなった</div>
    <div class="tag" onclick="toggleTag(this)">痛みが和らいだ</div>
    <div class="tag" onclick="toggleTag(this)">自分の体のクセがわかった</div>
    <div class="tag" onclick="toggleTag(this)">これからも継続したい</div>
  </div>

  <button class="btn-submit" onclick="generateReview()">🪄 AIでGoogle口コミ文章を作成</button>

  <div class="result-box" id="result-box">
    <strong>【生成された口コミ文章案】</strong>
    <p id="review-text" style="font-size: 0.9rem; margin-top: 8px; color: #166534; line-height: 1.6;"></p>
    <button class="btn-copy" onclick="copyAndRedirect()">📋 文章をコピーしてGoogleレビューへ投稿</button>
  </div>
</div>

<script>
  function toggleTag(el) {
    el.classList.toggle('active');
  }

  function generateReview() {
    const activeTags = Array.from(document.querySelectorAll('.tag.active')).map(e => e.innerText);
    if (activeTags.length === 0) {
      alert('1つ以上の項目を選択してください。');
      return;
    }
    
    const text = '半蔵門駅前整体院さんで' + activeTags.slice(0, 2).join('や') + 'の相談をさせていただきました。' + 
                 '丁寧なカウンセリングと説明で安心して施術を受けられました。終わった後は' + 
                 (activeTags.includes('体がとても軽くなった') ? '体がとても軽くなり、' : '') + 
                 '大満足です。駅からも近くて通いやすいので、これからも継続してメンテナンスをお願いしたいと思います！';
    
    document.getElementById('review-text').innerText = text;
    document.getElementById('result-box').style.display = 'block';
  }

  function copyAndRedirect() {
    const text = document.getElementById('review-text').innerText;
    navigator.clipboard.writeText(text).then(() => {
      alert('文章をコピーしました！表示されるGoogle画面に貼り付けて投稿してください。');
      // 半蔵門駅前整体院様のGoogleプレイスクチコミ投稿ダイレクトURL
      window.location.href = "https://search.google.com/local/writereview?placeid=ChIJBYKHkLSNGGAR3hJptwrYBnY";
    });
  }
</script>

</body>
</html># -
半蔵門口コミ用
