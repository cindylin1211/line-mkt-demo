<!DOCTYPE html>
<html lang="zh-TW">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AWS LINE官方帳號</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: #f5f5f5;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .phone-container {
            width: 375px;
            height: 812px;
            background: #000;
            border-radius: 25px;
            padding: 8px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.3);
        }

        .screen {
            width: 100%;
            height: 100%;
            background: #fff;
            border-radius: 20px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }

        .status-bar {
            height: 44px;
            background: #00c851;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 20px;
            color: white;
            font-size: 14px;
            font-weight: 600;
        }

        .line-header {
            height: 60px;
            background: #00c851;
            display: flex;
            align-items: center;
            padding: 0 15px;
            color: white;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .line-header .back-btn {
            font-size: 18px;
            margin-right: 15px;
            cursor: pointer;
        }

        .line-header .account-info {
            display: flex;
            align-items: center;
            flex: 1;
        }

        .line-header .avatar {
            width: 35px;
            height: 35px;
            background: linear-gradient(135deg, #ff9900, #232f3e);
            border-radius: 50%;
            margin-right: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 14px;
        }

        .line-header .name {
            font-size: 16px;
            font-weight: 600;
        }

        .chat-area {
            flex: 1;
            overflow-y: auto;
            padding: 15px;
            background: #f8f9fa;
        }

        .message {
            margin-bottom: 15px;
            display: flex;
            align-items: flex-start;
        }

        .message.bot {
            justify-content: flex-start;
        }

        .message.user {
            justify-content: flex-end;
        }

        .message-bubble {
            max-width: 80%;
            padding: 12px 16px;
            border-radius: 18px;
            font-size: 15px;
            line-height: 1.4;
            word-wrap: break-word;
        }

        .message.bot .message-bubble {
            background: #fff;
            color: #333;
            border-bottom-left-radius: 5px;
            box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
        }

        .message.user .message-bubble {
            background: #00c851;
            color: white;
            border-bottom-right-radius: 5px;
        }

        .message-time {
            font-size: 11px;
            color: #999;
            margin-top: 5px;
            text-align: right;
        }

        .bot-avatar {
            width: 35px;
            height: 35px;
            background: linear-gradient(135deg, #ff9900, #232f3e);
            border-radius: 50%;
            margin-right: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: white;
            font-size: 14px;
            flex-shrink: 0;
        }

        .input-area {
            height: 70px;
            background: #fff;
            border-top: 1px solid #e5e5ea;
            display: flex;
            align-items: center;
            padding: 0 15px;
            gap: 10px;
        }

        .message-input {
            flex: 1;
            height: 40px;
            border: 1px solid #ddd;
            border-radius: 20px;
            padding: 0 15px;
            font-size: 15px;
            outline: none;
        }

        .send-btn {
            width: 40px;
            height: 40px;
            background: #00c851;
            border: none;
            border-radius: 50%;
            color: white;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .menu-area {
            height: 180px;
            background: #fff;
            border-top: 1px solid #e5e5ea;
            padding: 15px;
        }

        .menu-grid {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            grid-template-rows: 1fr 1fr;
            gap: 10px;
            height: 100%;
        }

        .menu-item {
            background: #f8f9fa;
            border: 1px solid #e5e5ea;
            border-radius: 12px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.2s ease;
            position: relative;
        }

        .menu-item:hover {
            background: #e8f5e8;
            border-color: #00c851;
        }

        .menu-icon {
            font-size: 24px;
            margin-bottom: 5px;
        }

        .menu-text {
            font-size: 12px;
            text-align: center;
            color: #333;
            font-weight: 500;
        }

        .level-1 {
            grid-row: 1;
            grid-column: 1;
        }

        .level-2 {
            grid-row: 2;
            grid-column: 1;
        }

        .level-3 {
            grid-row: 2;
            grid-column: 2;
        }

        .level-4 {
            grid-row: 1;
            grid-column: 2;
        }

        .podcast {
            grid-row: 1;
            grid-column: 3;
        }

        .events {
            grid-row: 2;
            grid-column: 3;
        }

        .typing-indicator {
            display: none;
            align-items: center;
            margin-bottom: 15px;
        }

        .typing-dots {
            background: #fff;
            border-radius: 18px;
            border-bottom-left-radius: 5px;
            padding: 12px 16px;
            margin-left: 43px;
            box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
        }

        .typing-dots span {
            display: inline-block;
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background: #999;
            margin: 0 2px;
            animation: typing 1.4s infinite;
        }

        .typing-dots span:nth-child(2) {
            animation-delay: 0.2s;
        }

        .typing-dots span:nth-child(3) {
            animation-delay: 0.4s;
        }

        @keyframes typing {

            0%,
            60%,
            100% {
                transform: translateY(0);
            }

            30% {
                transform: translateY(-10px);
            }
        }

        .hidden {
            display: none;
        }
    </style>
</head>

<body>
    <div class="phone-container">
        <div class="screen">
            <div class="status-bar">
                <span>9:41</span>
                <span>📶 📶 📶 🔋</span>
            </div>

            <div class="line-header">
                <div class="back-btn">‹</div>
                <div class="account-info">
                    <div class="avatar">AWS</div>
                    <div class="name">AWS官方帳號</div>
                </div>
            </div>

            <div class="chat-area" id="chatArea">
                <!-- 訊息會在這裡動態生成 -->
            </div>

            <div class="typing-indicator" id="typingIndicator">
                <div class="bot-avatar">AWS</div>
                <div class="typing-dots">
                    <span></span>
                    <span></span>
                    <span></span>
                </div>
            </div>

            <div class="input-area">
                <input type="text" class="message-input" id="messageInput" placeholder="輸入訊息...">
                <button class="send-btn" id="sendBtn" onclick="sendMessage()">
                    ➤
                </button>
            </div>

            <div class="menu-area">
                <div class="menu-grid">
                    <div class="menu-item level-1" onclick="selectMenu('level1')">
                        <div class="menu-icon">💰</div>
                        <div class="menu-text">精打細算專區</div>
                    </div>

                    <div class="menu-item level-2" onclick="selectMenu('level2')">
                        <div class="menu-icon">🏥</div>
                        <div class="menu-text">雲端健康檢查</div>
                    </div>

                    <div class="menu-item level-3" onclick="selectMenu('level3')">
                        <div class="menu-icon">📡</div>
                        <div class="menu-text">政府補助雷達</div>
                    </div>

                    <div class="menu-item level-4" onclick="selectMenu('level4')">
                        <div class="menu-icon">🤖</div>
                        <div class="menu-text">AI助力配對器</div>
                    </div>

                    <div class="menu-item podcast" onclick="selectMenu('podcast')">
                        <div class="menu-icon">🎧</div>
                        <div class="menu-text">Podcast</div>
                    </div>

                    <div class="menu-item events" onclick="selectMenu('events')">
                        <div class="menu-icon">🎉</div>
                        <div class="menu-text">最新活動</div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        let currentStep = 'welcome';
        let userType = '';
        let isWaitingForInput = false;

        // 所有回應的映射表
        const responses = {
            // 身份相關
            'Developer': '歡迎開發人員！',
            'Engineer': '歡迎工程師！',
            'Security': '歡迎資安專業人員！',
            'SA': '歡迎系統架構師！',
            'IT Pro': '歡迎IT專業人員！',
            'TDM': '歡迎創辦人或經營決策者！',
            'Business Pro': '歡迎採購、財務或業務相關人員！',
            'Educate': '歡迎學生、教職或研究員！',
            '帳戶問題': '關於帳戶問題，我們會為您轉接專業人員協助。',
            'Other': '感謝您的參與！',

            // 關卡觸發詞
            '成本': `您每月 IT 支出大約多少呢？
A. 0-1萬 
B. 1-5萬 
C. 5-10萬 
D. 10萬以上`,

            '雲端': `您目前主要系統在哪邊呢？
M. 自建機房
N. 其他雲端
O. 混合架構
P. 主機代管`,

            '補助': `您公司的資本額是？
Y. 未滿1億
Z. 1-5 億
1. 5-10 億
2. 10 億以上`,

            'AI': `您的團隊主要面臨哪種工作壓力？
11. 重複性作業太多
12. 資料分析繁瑣
13. 客戶回應過多
14. 需要創意思考`,

            // 關卡1選項 (A-L)
            'A': '您的基礎架構成本很輕盈，適合先用免費方案測試 !\n\n您的公司員工人數大約多少人呢？\nE. 1-10人 \nF. 11-50人 \nG. 51-200人 \nH. 200人以上',
            'B': '您可能可以省下約 20%，一年就是一筆額外預算 !\n\n您的公司員工人數大約多少人呢？\nE. 1-10人 \nF. 11-50人 \nG. 51-200人 \nH. 200人以上',
            'C': '您已經有中型規模，導入雲端一年能幫您省下 50–100 萬!\n\n您的公司員工人數大約多少人呢？\nE. 1-10人 \nF. 11-50人 \nG. 51-200人 \nH. 200人以上',
            'D': '您屬於大型支出，用雲端優化能帶來百萬級成本差異!\n\n您的公司員工人數大約多少人呢？\nE. 1-10人 \nF. 11-50人 \nG. 51-200人 \nH. 200人以上',

            'E': '小而靈活的團隊，最適合先用輕量雲端方案快速啟動，避免一開始就燒太多成本~\n\n您最關心哪項成本呢？\nI. 伺服器 \nJ. 儲存空間 \nK. 網路頻寬 \nL. 維護人力',
            'F': '是快速成長的關鍵階段，導入雲端能幫您把人力從 IT 維運釋放出來，專心衝業務 !\n\n您最關心哪項成本呢？\nI. 伺服器 \nJ. 儲存空間 \nK. 網路頻寬 \nL. 維護人力',
            'G': '您已經有中型規模，這時候優化基礎建設能帶來明顯的省成本與效率提升!\n\n您最關心哪項成本呢？\nI. 伺服器 \nJ. 儲存空間 \nK. 網路頻寬 \nL. 維護人力',
            'H': '您屬於大型組織，雲端可以幫您在成本控管與跨部門協作上更有彈性，避免傳統架構綁手綁腳!\n\n您最關心哪項成本呢？\nI. 伺服器 \nJ. 儲存空間 \nK. 網路頻寬 \nL. 維護人力',

            'I': '伺服器其實是雲端能最快幫您省下的成本，因為您不用再預先買硬體，而是用多少付多少!\n\n輸入「節省」獲得成本節省相關資訊!',
            'J': '資料量成長快？雲端儲存能彈性擴容，避免您一次花大錢買設備卻又用不滿 !\n\n輸入「節省」獲得成本節省相關資訊!',
            'K': '雲端方案能依流量自動調整，不用再擔心高峰期頻寬爆掉或閒置浪費 !\n\n輸入「節省」獲得成本節省相關資訊!',
            'L': '交給雲端服務商代管，您的 IT 團隊就能專心做更有價值的事，而不是天天救火！\n\n輸入「節省」獲得成本節省相關資訊!',

            // 關卡2選項 (M-X)
            'M': '您的系統高度依賴自建機房，適合先了解雲端過渡方案！\n\n您最擔心什麼呢？\nQ. 資料安全\nR. 服務中斷\nS. 技術難度 \nT. 成本超支',
            'N': '您已經開始使用雲端，下一步可以優化整合與安全管理！\n\n您最擔心什麼呢？\nQ. 資料安全\nR. 服務中斷\nS. 技術難度 \nT. 成本超支',
            'O': '混合架構可以兼顧彈性與控制，看看是否還能進一步優化！\n\n您最擔心什麼呢？\nQ. 資料安全\nR. 服務中斷\nS. 技術難度 \nT. 成本超支',
            'P': '您使用代管服務，考慮雲端方案能提升成本效益！\n\n您最擔心什麼呢？\nQ. 資料安全\nR. 服務中斷\nS. 技術難度 \nT. 成本超支',

            'Q': '資料安全是關鍵，AWS 提供多層防護讓您放心上雲！\n\n您有技術團隊嗎？\nU. 專職 IT\nV. 外包\nW. 老闆自己來 \nX. 還沒規劃',
            'R': '系統穩定性很重要，雲端自動備援幫您減少中斷風險！\n\n您有技術團隊嗎？\nU. 專職 IT\nV. 外包\nW. 老闆自己來 \nX. 還沒規劃',
            'S': '技術門檻高？AWS 提供簡單易上手的方案！\n\n您有技術團隊嗎？\nU. 專職 IT\nV. 外包\nW. 老闆自己來 \nX. 還沒規劃',
            'T': '成本可控，按需付費避免浪費！\n\n您有技術團隊嗎？\nU. 專職 IT\nV. 外包\nW. 老闆自己來 \nX. 還沒規劃',

            'U': '有專業團隊，可以進一步導入自動化與管理最佳實踐！\n\n輸入「AWS」獲得雲端健檢相關資訊!',
            'V': '外包團隊穩定性高，但可用雲端工具降低管理複雜度！\n\n輸入「AWS」獲得雲端健檢相關資訊!',
            'W': '老闆辛苦啦！雲端方案可以幫您分擔維運壓力！\n\n輸入「AWS」獲得雲端健檢相關資訊!',
            'X': '沒團隊也沒關係，AWS 提供簡單快速上手的方案！\n\n輸入「AWS」獲得雲端健檢相關資訊!',

            // 關卡3選項 (Y,Z,1-10)
            'Y': '小型企業也有專屬補助，來看看有哪些適合您！\n\n曾經申請過補助嗎？\n3. 有，成功\n4. 有，失敗\n5. 沒有，不知道有政府補助\n6. 沒有，不知道怎麼申請',
            'Z': '這類型企業補助很多，抓住資金支援機會！\n\n曾經申請過補助嗎？\n3. 有，成功\n4. 有，失敗\n5. 沒有，不知道有政府補助\n6. 沒有，不知道怎麼申請',
            '1': '規模較大，可申請多元專案補助！\n\n曾經申請過補助嗎？\n3. 有，成功\n4. 有，失敗\n5. 沒有，不知道有政府補助\n6. 沒有，不知道怎麼申請',
            '2': '大型企業補助有限，但可申請策略型或產業創新計畫！\n\n曾經申請過補助嗎？\n3. 有，成功\n4. 有，失敗\n5. 沒有，不知道有政府補助\n6. 沒有，不知道怎麼申請',

            '3': '太棒了！您已經有經驗，可以考慮申請更高額或多元補助方案！\n\n希望我們協助嗎？\n7. 全程代辦\n8. 部分協助\n9. 自己處理\n10. 還沒規劃',
            '4': '別氣餒！可能是申請方式或資料不完整，AWS/政府資源能幫您增加成功率！\n\n希望我們協助嗎？\n7. 全程代辦\n8. 部分協助\n9. 自己處理\n10. 還沒規劃',
            '5': '沒關係，現在就來了解您能申請的補助類別，別錯過資金支援！\n\n希望我們協助嗎？\n7. 全程代辦\n8. 部分協助\n9. 自己處理\n10. 還沒規劃',
            '6': '別擔心，補助申請流程其實有方法，我們可以一步步協助您！\n\n希望我們協助嗎？\n7. 全程代辦\n8. 部分協助\n9. 自己處理\n10. 還沒規劃',

            '7': '沒問題！我們可以全程協助，幫您省時又省力，讓您專注核心業務！\n\n輸入「懶人包」獲得政府補助懶人包!',
            '8': '好的，我們可以提供部分支援，輔助您順利完成申請流程！\n\n輸入「懶人包」獲得政府補助懶人包!',
            '9': '了解，您可以自行操作，我們也提供資源與指南給您參考！\n\n輸入「懶人包」獲得政府補助懶人包!',
            '10': '沒關係，我們可以先幫您評估適合方案，再決定是否申請！\n\n輸入「懶人包」獲得政府補助懶人包!',

            // 關卡4選項 (11-22)
            '11': 'AI 可以幫您自動化日常作業，釋放大量人力！\n\n您最希望 AI 達成的效果是？\n15. 降低人力成本\n16. 提升效率\n17. 增加營收\n18. 風險控制',
            '12': 'AI 助手可快速整理與分析資料，提升效率！\n\n您最希望 AI 達成的效果是？\n15. 降低人力成本\n16. 提升效率\n17. 增加營收\n18. 風險控制',
            '13': 'AI 聊天機器人能協助回覆客戶，提高服務速度！\n\n您最希望 AI 達成的效果是？\n15. 降低人力成本\n16. 提升效率\n17. 增加營收\n18. 風險控制',
            '14': 'AI 可以提供靈感與建議，輔助創意思考！\n\n您最希望 AI 達成的效果是？\n15. 降低人力成本\n16. 提升效率\n17. 增加營收\n18. 風險控制',

            '15': '導入 AI 後，您可以把團隊從重複性工作中解放出來，專注核心業務！\n\n您何時考慮導入？\n19. 馬上\n20. 3 個月內\n21. 半年內\n22. 還在評估',
            '16': 'AI 可以自動化資料處理與流程，加快工作節奏，節省時間！\n\n您何時考慮導入？\n19. 馬上\n20. 3 個月內\n21. 半年內\n22. 還在評估',
            '17': 'AI 助力決策與行銷策略，讓您抓住更多商機！\n\n您何時考慮導入？\n19. 馬上\n20. 3 個月內\n21. 半年內\n22. 還在評估',
            '18': 'AI 幫您監控風險、預測異常，降低決策失誤！\n\n您何時考慮導入？\n19. 馬上\n20. 3 個月內\n21. 半年內\n22. 還在評估',

            '19': '太好了！您可以立即體驗 AI 效益，快速釋放人力與提升效率！\n\n輸入「效率」解鎖AI為您帶來的價值!',
            '20': '很棒！有短期規劃，AI 導入能讓您在短時間看到成果！\n\n輸入「效率」解鎖AI為您帶來的價值!',
            '21': '中期規劃很合理，我們可以先協助評估最適合的導入場景！\n\n輸入「效率」解鎖AI為您帶來的價值!',
            '22': '沒問題，我們可以提供參考資料，幫助您判斷 AI 導入的最佳時機！\n\n輸入「效率」解鎖AI為您帶來的價值!',

            // 最終關鍵字
            '節省': '根據您的回答，導入雲端平均可幫您省下 20–35% IT 成本，而且費用更彈性! 同時，您的團隊能省下至少 30% 維運時間，更專注在核心業務~ 想知道完整節省細節？填表單諮詢! (插入landing page link)',

            'AWS': '您的雲端成熟度正在努力加速中 ! 推薦使用 AWS 客製化方案，安全快速上雲~ 想更深入了解您的雲端健康狀況？填表單預約！(插入landing page link)',

            '懶人包': '想下載最新版本政府補助懶人包？快點選連結領取！\nhttps://pages.awscloud.com/aws-gov-fund-registration.html',

            '效率': '根據您的回答， 您的最佳 AI 導入場景可節省約 30% 工時! 降低成本的同時大幅提升效率! 想領取完整 AI 建議與成功案例？填表單諮詢！(插入landing page link)'
        };

        // 初始化
        window.onload = function() {
            setTimeout(showWelcomeMessage, 1000);
        };

        function addMessage(content, isUser = false, delay = 0) {
            setTimeout(() => {
                const chatArea = document.getElementById('chatArea');
                const messageDiv = document.createElement('div');
                messageDiv.className = `message ${isUser ? 'user' : 'bot'}`;

                const now = new Date();
                const timeString = now.getHours().toString().padStart(2, '0') + ':' +
                    now.getMinutes().toString().padStart(2, '0');

                if (isUser) {
                    messageDiv.innerHTML = `
                        <div class="message-bubble">
                            ${content}
                            <div class="message-time">${timeString}</div>
                        </div>
                    `;
                } else {
                    messageDiv.innerHTML = `
                        <div class="bot-avatar">AWS</div>
                        <div class="message-bubble">
                            ${content.replace(/\n/g, '<br>')}
                            <div class="message-time">${timeString}</div>
                        </div>
                    `;
                }

                chatArea.appendChild(messageDiv);
                chatArea.scrollTop = chatArea.scrollHeight;
            }, delay);
        }

        function showTyping() {
            document.getElementById('typingIndicator').style.display = 'flex';
            const chatArea = document.getElementById('chatArea');
            chatArea.scrollTop = chatArea.scrollHeight;
        }

        function hideTyping() {
            document.getElementById('typingIndicator').style.display = 'none';
        }

        function showWelcomeMessage() {
            showTyping();
            setTimeout(() => {
                hideTyping();
                const message = `熱烈歡迎~您已成爲AWS亞馬遜雲端聚落的一員！快來告訴我們你是何方大大~

• 開發人員，輸入：Developer
• 工程師，輸入：Engineer  
• 資安專業人員，輸入：Security
• 系統架構師，輸入：SA
• IT專業人員或技術支援經理，輸入：IT Pro
• 創辦人或經營決策者，輸入：TDM
• 採購、財務或是業務相關人員，輸入：Business Pro
• 學生、教職或研究員，輸入：Educate
• 帳戶相關疑問，輸入：帳戶問題
• 其他，輸入：Other`;

                addMessage(message);
                currentStep = 'getUserType';
                isWaitingForInput = true;
            }, 2000);
        }

        function sendMessage() {
            const input = document.getElementById('messageInput');
            const message = input.value.trim();
            if (!message) return;

            addMessage(message, true);
            input.value = '';

            // 處理輸入
            handleUserInput(message);
        }

        function handleUserInput(message) {
            // 如果是在等待身份輸入的階段
            if (currentStep === 'getUserType' && isWaitingForInput) {
                userType = message;
                showWelcomeToGame();
                return;
            }

            // 檢查是否有對應的回應（包括身份選項和所有選項代號）
            const upperMessage = message.toUpperCase();
            
            if (responses[message] || responses[upperMessage]) {
                showTyping();
                setTimeout(() => {
                    hideTyping();
                    const response = responses[message] || responses[upperMessage];
                    addMessage(response);
                }, 1000);
            } else {
                // 沒有找到對應回應，但不顯示錯誤訊息，保持沉默
                // 這樣用戶可以繼續嘗試其他輸入
            }
        }

        function showWelcomeToGame() {
            isWaitingForInput = false;
            showTyping();
            setTimeout(() => {
                hideTyping();
                const message = `🎮 歡迎加入 AWS 雲端成長之旅！

在這裡您可以體驗：
💰 精打細算專區 - 計算雲端為您省下的成本
🏥 雲端健康檢查 - 檢查您的IT健康指數  
📡 政府補助雷達 - 找出適合的補助方案
🤖 AI助力配對器 - 發現AI為您帶來的價值

點擊下方選單開始探索!讓 AWS 協助您的事業更上一層樓!`;

                addMessage(message);
                currentStep = 'ready';
            }, 1500);
        }

        function selectMenu(menuType) {
            switch (menuType) {
                case 'level1':
                    addMessage('精打細算專區', true);
                    handleUserInput('成本');
                    break;
                case 'level2':
                    addMessage('雲端健康檢查', true);
                    handleUserInput('雲端');
                    break;
                case 'level3':
                    addMessage('政府補助雷達', true);
                    handleUserInput('補助');
                    break;
                case 'level4':
                    addMessage('AI助力配對器', true);
                    handleUserInput('AI');
                    break;
                case 'podcast':
                    showPodcast();
                    break;
                case 'events':
                    showEvents();
                    break;
            }
        }

        function showPodcast() {
            addMessage('Podcast', true);
            showTyping();
            setTimeout(() => {
                hideTyping();
                addMessage('🎧 AWS Podcast 精選內容：\n\n📻 雲端新手指南 - 第12集\n「雲端安全最佳實踐」\n\n📻 技術深度解析 - 第8集\n「容器化部署策略」\n\n點擊連結收聽更多：\nhttps://aws.amazon.com/tw/podcasts/');
            }, 1500);
        }

        function showEvents() {
            addMessage('最新活動', true);
            showTyping();
            setTimeout(() => {
                hideTyping();
                addMessage('🎉 AWS最新活動資訊：\n\n📅 AWS雲端技術峰會\n時間：2025年9月15日\n地點：台北國際會議中心\n\n📅 免費雲端工作坊\n時間：每週三晚上 7:00\n形式：線上直播\n\n立即報名：\nhttps://aws.amazon.com/tw/events/');
            }, 1500);
        }

        // Enter鍵發送
        document.getElementById('messageInput').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                sendMessage();
            }
        });
    </script>
</body>

</html>
