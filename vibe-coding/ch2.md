## 前言

### AI 在開發中的角色與潛力

生成式 AI 作為輔助生成的工具，像是 ChatGPT 或 Claude，都是以「聊天」的方式進行，提供 Prompt 給 AI，AI 會以「聊天」的方式回覆我們。

Prompt 之下得到的答案，很多很棒很驚艷，像是很多書本提到的原則與範例，有需多很棒的範例，拿來做文案、企劃生成是蠻不錯的方式。

AI 生成內容的隨機性既是優點也是缺點。這種「LLM 串接詞語的隨機性」讓每次產出都充滿驚喜，特別適合創意發想階段，能突破人類思維的框架限制。然而在技術開發領域，這種不穩定性就成為致命傷。拿來做創意性質的內容，像是文案、企劃是蠻不錯的方式，但拿來做技術開發，就會遇到蠻大的瓶頸，至於瓶頸在哪，我們後面再談。

這邊先看幾個 AI 輔助開發的「優良範例」：

比方說，以下是這次新增的 API 程式碼，我希望可以請 AI 幫我產出一份技術文件：

```
const express = require('express');
const router = express.Router();

// 模擬資料庫中的電子郵件資料
const emails = [
  { id: 1, subject: '歡迎信', from: 'service@example.com' },
  { id: 2, subject: '訂單確認', from: 'orders@example.com' },
  { id: 3, subject: '促銷活動', from: 'marketing@example.com' }
];

router.get('/emails', (req, res) => {
  try {
    // 回傳電子郵件清單
    res.status(200).json({
      success: true,
      data: emails
    });
  } catch (error) {
    res.status(500).json({
      success: false,
      message: '取得郵件清單時發生錯誤'
    });
  }
});
module.exports = router;
```

- 技術文件：第一次，提供粗略的指令，我希望 AI 「自由發揮」，產出一份技術文件：

```
請 AI 幫我根據此 API 程式碼產出一份技術文件：
```

產出結果
```
以下是根据提供的 API 代码生成的技術文件，使用 Markdown 格式呈現：

---

# API 技術文件：電子郵件清單

## 概述
此 API 提供一個簡單的端點，用於獲取模擬的電子郵件清單。它基於 Express.js 框架，並以 JSON 格式返回資料。

## 端點
- **路徑**: `/emails`
- **方法**: `GET`

## 請求範例
```bash
curl -X GET http://yourdomain.com/emails
```

## 參數
此端點無需任何查詢參數或請求體。

### 關鍵功能
1. **模擬資料庫**:
   - 使用一個靜態陣列 `emails` 模擬資料庫中的電子郵件資料。
2. **錯誤處理**:
   - 使用 `try-catch` 區塊捕獲可能的錯誤，並返回適當的錯誤訊息。

## 使用情境
- 適用於需要快速獲取電子郵件清單的前端應用。
- 可用於測試或原型開發階段。

## 注意事項
- 此 API 僅為範例，實際應用中應替換為真實的資料庫查詢邏輯。
- 錯誤處理部分可根據需求進一步擴展，例如記錄錯誤日誌或發送警報。

--- [以上可以補上 Prompt 截圖]

總的來說，AI 產這樣很棒了！ 雖然不盡完美，但有總比沒有好。可以省下很多「行政作業」時間，而且產出的內容也蠻不錯，至少是一份蠻完整的 API 技術文件，應有盡有。

第二次，也是提供一樣的 Prompt 指令，得到這樣的答案：
```
以下是根据提供的 API 代码生成的技術文件，使用 Markdown 格式呈現：

---

# API 技術文件：電子郵件清單

## 概述  
此 API 提供一個簡單的端點，用於獲取模擬的電子郵件清單。它基於 Express.js 框架，並以 JSON 格式返回資料。

## 端點  
- **路徑**: `/emails`  
- **方法**: `GET`  

## 請求範例  
```bash
curl -X GET http://yourdomain.com/emails
```

## 參數  
此端點無需任何查詢參數或請求體。

## 關鍵功能  
1. **模擬資料庫**:  
   - 使用一個靜態陣列 `emails` 模擬資料庫中的電子郵件資料。  
2. **錯誤處理**:  
   - 使用 `try-catch` 區塊捕獲可能的錯誤，並返回適當的錯誤訊息。  

## 使用情境  
- 適用於需要快速獲取電子郵件清單的前端應用。  
- 可用於測試或原型開發階段。  

## 注意事項  
- 此 API 僅為範例，實際應用中應替換為真實的資料庫查詢邏輯。  
- 錯誤處理部分可根據需求進一步擴展，例如記錄錯誤日誌或發送警報。  

---

### 補充說明  
- **資料格式**:  
  返回的資料格式為 JSON，包含以下欄位：  
  - `success`: 布林值，表示請求是否成功。  
  - `data`: 電子郵件清單的陣列，每封郵件包含 `id`、`subject` 和 `from` 欄位。  
  - `message` (錯誤時): 錯誤訊息。  

- **擴展建議**:  
  - 若需支援分頁或篩選功能，可新增查詢參數（如 `limit`、`offset` 或 `subject`）。  
  - 考慮加入身份驗證機制（如 JWT）以保護端點。  

如果需要進一步調整或補充內容，請隨時告知！

---

這兩次的回覆乍看之下都不錯，但仔細看會發現，第二次的回覆比較完整，而且更符合我們的期望。而如果每次都要手動調整，這樣的效率太低了，所以這邊我們需要建立一個「Prompt 品質控制」機制，讓 AI 產出的內容更符合我們的期望。
讓生成的內容變成「可控」的，這樣我們就可以更有效地使用 AI 來輔助我們的開發工作。


## Vibe Coding 的流程

### 前言 -- AI 生成程式碼的品質控制

那麼，Vibe Coding 的流程是怎麼樣呢？

剛剛提到，我們需要建立一個「Prompt 品質控制」機制，讓 AI 產出的內容更符合我們的期望。而這又跟我們的主題「Vibe Coding」的流程有什麼關係？

當然有關係，雖然我們可以預期 AI 產出的程式碼「每次」都不太一樣，但至少要維持在一定的品質。這有點像是請不同同事寫程式碼，雖然每個同事寫的程式碼，實作細節都不太一樣，但至少都會要求在一定的品質。否則 Code Review 的時候，就會被打槍。

而當 AI 產出程式碼後，由提交 Prompt 的開發者需擔任第一道品質把關者。這包含一些基本的檢查，像是：

1. **技術正確性驗證**：檢查程式碼是否符合預期功能，特別注意邊界條件和效能考量，是不是 AI 生成的程式碼有符合目前專案的技術要求。
2. **風格一致性審查**：確保符合團隊的 coding style 和架構模式，這邊包含像是命名規則、程式碼風格、架構模式等。
3. **上下文適配性**：確認產出內容與當前專案需求相符，生成的程式碼是否有跟專案的脈絡 domain know how 相符。

這過程類似 Code Review，但更專注於「Prompt 與產出」的對應關係。如果每次生成品質參差不齊，我們開發者需要建立個檢查清單，例如：
- 是否正確實現了需求？
- 是否有潛在的效能瓶頸？
- 是否符合安全規範？

雖然透過這種機制，我們能逐步建立「可預期的 AI 協作模式」，讓 AI 成為更可靠。但每次都要這樣「人工」檢查，實在太累了、效率太低了！

因此，我們會希望 AI 能夠自動控管品質，可以產出「我們腦中預想的」內容，然而如同上述所說，AI 產出的內容，常常會跟我們預想的有所出入，這邊再舉個比較簡單且具體的範例。

我希望 AI 幫我實作 Fibonnaci 數列，但 AI 產出的內容，可能是實作出 Fibonnaci 數列的遞迴版本，而非更好的迴圈＋記憶版本。
或者，又像是上一章節提到的產出 API 技術文件，如果每次下指令產出的結果不一致，都還要手動調整，光想就很累呀。

說了這麼多，我們到底要怎麼辦？
所以我們需要建立一個「Prompt 品質控制」機制，讓 AI 產出的內容更符合我們的期望。

### Prompt Engineering 基礎 -- 設定 Prompt 原則

首先是建立原則，想方設法讓 AI 產出的內容更符合我們的期望，首要的目的是「穩定性」。

而我們要先認識到，為什麼 AI 產出的內容會有這些問題呢？ 主要在於 LLM 的「幻想問題」(Hallucination)：

1. **技術準確性**：AI 可能生成看似合理但實際上錯誤的技術內容，這是因為 LLM 的訓練資料包含了大量的網路資料，這些資料可能包含錯誤、過時的資訊，而 LLM 會「自信地」呈現這些不準確的資訊。
2. **一致性缺失**：相同 prompt 在不同時間可能產出不同結果
3. **上下文斷裂**：長對話中可能遺忘或扭曲先前討論的脈絡細節，導致後續的回答不一致。

有沒有發現，這些問題其實跟我們在開發中遇到的問題很相似？ 沒錯，就是因為目前 LLM 技術上的「限制」，導致這些問題的發生，讓我們不得不面對這些問題，以提高生成的品質與穩定。

這種特性使得：
- 技術文件可能包含不準確的 API 用法
- 程式碼範例可能有隱藏的邏輯錯誤
- 系統架構建議可能忽略關鍵限制條件

更棘手的是，AI 通常會「自信地」呈現這些不準確的資訊，讓初學者難以辨別真偽，難以判別 AI 給的答案是否是「真的有用」，還只是「看似有用」，實際上是「結構優良」的無用程式碼。

這正是為什麼在專業開發中，我們需要建立「Prompt 品質控制」機制，而非完全放任 AI 自由生成答案。


### 設定 Prompt 原則

首先，要教大家幾個 Prompt 的基礎原則，首先是 Prompt 的「結構」。

最基本的結構，是「無序清單」和「有序清單」。將我們的期望，以清單的方式列出，讓 AI 知道我們的期望。這在寫程式碼生成時，特別好用，也蠻常見的，像是：

以無序清單提供說明，像是：
```
請幫我設計一個註冊表單，包含以下功能：
  - 使用者名稱
  - 使用者密碼
  - 使用者信箱
```
如此一來，AI 會知道我們的期望，總共有這些「具體」該實現的項目。比較不會讓 AI 「自由發揮」，產出不符合我們期望的內容。畢竟寫程式不是隨興創作，而是要解決我們的問題，希望 AI 可以照我們腦中想的，精準實作出來。

以下是上面的 Prompt 的結果，AI 產出一份 HTML Form 表單，但實際上我是想要請 AI 產出一份「使用 React Hook Form 的 React 表單元件」，可以看到說，雖然產出的結果姑且算是「可以用」，但不是我們想要的，還不夠精準。
```
<form>
  <div class="form-group">
    <label for="username">使用者名稱</label>
    <input type="text" id="username" name="username" required>
  </div>
  
  <div class="form-group">
    <label for="password">使用者密碼</label>
    <input type="password" id="password" name="password" required>
  </div>
  
  <div class="form-group">
    <label for="email">使用者信箱</label>
    <input type="email" id="email" name="email" required>
  </div>
  
  <button type="submit">註冊</button>
</form>
```

進一步呢，無序清單還可以補充「子清單」的說明，像是：
```
請幫我設計一個註冊表單，包含以下功能：
  - 以 React Hook Form 實作
    - 以 React 實作
    - 元件使用 Shadcn 的 UI 元件
  - 使用者名稱
    - 必填
    - 長度限制 20 個字
  - 使用者密碼
    - 必填
    - 長度限制 8 ~ 16 個字
  - 使用者信箱
    - 必填
    - 長度限制 10 個字，驗證格式為 email。
```

以下是上述 Prompt 結果的「部分節錄」，可以看到說，這樣的結果不只符合我們的期望了，且相當完整，幾乎是「可以開箱即用」的成品了！
```
import { useForm } from "react-hook-form";
import { Button } from "@/components/ui/button";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Input } from "@/components/ui/input";

export function RegisterForm() {
  const form = useForm({
    defaultValues: {
      username: "",
      password: "",
      email: "",
    },
  });

  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <Form {...form}>
      <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-4">
        // ...
        <FormField
          control={form.control}
          name="email"
          rules={{
            required: "電子郵件為必填",
            maxLength: {
              value: 10,
              message: "電子郵件不能超過10個字",
            },
            pattern: {
              value: /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i,
              message: "請輸入有效的電子郵件格式",
            },
          }}
          render={({ field }) => (
            <FormItem>
              <FormLabel>使用者信箱</FormLabel>
              <FormControl>
                <Input type="email" placeholder="請輸入電子郵件" {...field} />
              </FormControl>
              <FormMessage />
            </FormItem>
          )}
        />

        <Button type="submit">註冊</Button>
      </form>
    </Form>
  );
}

```

總的來說，無序清單可以提供「具體」的說明，讓 AI 知道我們的期望。此外，清單還可以補充「子清單」的說明，讓 AI 知道我們的期望更精確，補充每一項的細節，細節越具體，使得產出的結果越符合我們的期望。


以有序清單提供步驟，像是：
請幫我設計一個註冊表單，包含以下步驟：
  - 步驟 1：設計表單結構
  - 步驟 2：設計表單樣式
  - 步驟 3：設計表單功能


無序清單和有序清單，都是蠻常見的 Prompt 結構，可以讓 AI 知道我們的期望。而這兩者的結合，可以讓 AI 知道我們的期望更精確，像是：
```
請幫我設計一個註冊表單，包含以下步驟：
  - 步驟 1：設計表單結構
    - 以 React Hook Form 實作
    - 以 React 實作
    - 元件使用 Shadcn 的 UI 元件
```
主要使用時機的差異，在於我們的期望是否需要有「順序」，像是表單的每個欄位需求，適合用「無序清單」，因為我們的期望每一項並沒有區分「先後順序」的必要：
- 表單需求 A
- 表單需求 B
- 表單需求 C

而如果我們的期望需要有「順序」，像是請 AI 幫我們實作一個功能，照一系列的操作步驟，以確保每一步的生成可以依照前一步的結果，逐步生成：
1. 先幫我根據需求，撰寫表單 UI 操作的「測試程式碼」。
2. 再幫我實作表單 UI 元件，執行測試程式碼，確保 UI 元件符合需求。
3. 最後依照此需求，撰寫技術文件。

這樣的清單，就是「有序清單」，因為我們的期望每一項都有「先後順序」的必要，且若不照此順序，會導致產出的結果不符合我們的期望，那就很適合用「有序清單」。

最後，提供一個相對完整，結合「無序清單」和「有序清單」的 Prompt 範例供大家參考，可以試試看將以下 Prompt 餵給 ChatGPT 或 Claude 嘗試看看，是否能夠產出更符合你期望的結果：

```
請幫我設計一個使用者註冊表單，包含以下規格：

  1. 設計表單結構
    - 以 React Hook Form 實作
    - 以 React 實作
    - 元件使用 Shadcn 的 UI 元件
    - 表單需要包含以下欄位：
      - 使用者名稱
        - 必填
        - 長度限制 20 個字
      - 使用者密碼
        - 必填
        - 長度限制 8 ~ 16 個字
      - 使用者信箱
        - 必填
        - 長度限制 10 個字，驗證格式為 email。
  2. 撰寫測試程式碼
    - 以 Jest 實作
    - 以 React Testing Library 實作
    - 元件使用 Shadcn 的 UI 元件
    - 測試程式碼需要包含所有可能的邊界條件
      - 使用者名稱：
        - 必填
        - 長度限制 20 個字
      - 使用者密碼：
        - 必填
        - 長度限制 8 ~ 16 個字
      - 使用者信箱：
        - 必填
        - 長度限制 10 個字，驗證格式為 email。
      - 按下註冊按鈕：
        - 若表單驗證通過，則顯示註冊成功訊息
        - 若表單驗證未通過，則顯示錯誤訊息
  3. 撰寫技術文件
    - 以 Markdown 格式撰寫
    - 技術文件需要包含所有可能的邊界條件，按照第一步驟的表單結構，撰寫每一個欄位的驗證規則。
```

以下是 Prompt 結果，可以看到說，這樣的結果比起上一個 Prompt 的結果，更符合我們的期望，且更完整。
```

import { useForm } from "react-hook-form";
import { Button } from "@/components/ui/button";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Input } from "@/components/ui/input";

export function RegisterForm() {
  const form = useForm({
    defaultValues: {
      username: "",
      password: "",
      email: "",
    },
  });

  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <Form {...form}>
      <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-4">
        <FormField
          control={form.control}
          name="username"
          rules={{
            required: "使用者名稱為必填",
            maxLength: {
              value: 20,
              message: "使用者名稱不能超過20個字",
            },
          }}
          render={({ field }) => (
            <FormItem>
              <FormLabel>使用者名稱</FormLabel>
              <FormControl>
                <Input placeholder="請輸入使用者名稱" {...field} />
              </FormControl>
              <FormMessage />
            </FormItem>
          )}
        />

        <FormField
          control={form.control}
          name="password"
          rules={{
            required: "密碼為必填",
            minLength: {
              value: 8,
              message: "密碼長度需至少8個字",
            },
            maxLength: {
              value: 16,
              message: "密碼長度不能超過16個字",
            },
          }}
          render={({ field }) => (
            <FormItem>
              <FormLabel>使用者密碼</FormLabel>
              <FormControl>
                <Input type="password" placeholder="請輸入密碼" {...field} />
              </FormControl>
              <FormMessage />
            </FormItem>
          )}
        />

        <FormField
          control={form.control}
          name="email"
          rules={{
            required: "電子郵件為必填",
            maxLength: {
              value: 10,
              message: "電子郵件不能超過10個字",
            },
            pattern: {
              value: /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i,
              message: "請輸入有效的電子郵件格式",
            },
          }}
          render={({ field }) => (
            <FormItem>
              <FormLabel>使用者信箱</FormLabel>
              <FormControl>
                <Input type="email" placeholder="請輸入電子郵件" {...field} />
              </FormControl>
              <FormMessage />
            </FormItem>
          )}
        />

        <Button type="submit">註冊</Button>
      </form>
    </Form>
  );
}
```

單元測試
```
import { render, screen, fireEvent } from "@testing-library/react";
import { RegisterForm } from "./RegisterForm";

describe("RegisterForm", () => {
  it("should validate username field", async () => {
    render(<RegisterForm />);
    const usernameInput = screen.getByPlaceholderText("請輸入使用者名稱");

    // 測試必填
    fireEvent.blur(usernameInput);
    expect(await screen.findByText("使用者名稱為必填")).toBeInTheDocument();

    // 測試長度限制
    fireEvent.change(usernameInput, { target: { value: "a".repeat(21) } });
    fireEvent.blur(usernameInput);
    expect(await screen.findByText("使用者名稱不能超過20個字")).toBeInTheDocument();
  });

  //...中間省略

  it("should submit the form if validation passes", async () => {
    render(<RegisterForm />);
    const usernameInput = screen.getByPlaceholderText("請輸入使用者名稱");
    const passwordInput = screen.getByPlaceholderText("請輸入密碼");
    const emailInput = screen.getByPlaceholderText("請輸入電子郵件");
    const submitButton = screen.getByText("註冊");

    fireEvent.change(usernameInput, { target: { value: "validuser" } });
    fireEvent.change(passwordInput, { target: { value: "validpassword" } });
    fireEvent.change(emailInput, { target: { value: "valid@email.com" } });
    fireEvent.click(submitButton);

    // 假設表單提交成功後會顯示成功訊息
    expect(console.log).toHaveBeenCalledWith({
      username: "validuser",
      password: "validpassword",
      email: "valid@email.com",
    });
  });
});
```

技術文件
```
# 使用者註冊表單技術文件

## 表單結構
- **框架**：React + React Hook Form
- **UI 元件庫**：Shadcn

### 欄位驗證規則
1. **使用者名稱**：
   - 必填。
   - 長度限制：最多 20 個字。
2. **使用者密碼**：
   - 必填。
   - 長度限制：8 ~ 16 個字。
3. **使用者信箱**：
   - 必填。
   - 長度限制：最多 10 個字。
   - 格式驗證：必須符合電子郵件格式。

## 測試案例
- 測試所有欄位的必填驗證。
- 測試欄位的長度限制。
- 測試電子郵件的格式驗證。
- 測試表單提交功能。

## 使用情境
- 適用於需要使用者註冊功能的前端應用。
- 可用於原型開發或正式產品。

```

以上是使用 DeepSeek 的 AI 產出的結果，雖然比起 Claude 最新版本或是其他高階的 AI 模型，產出的結果較不完整，但已經是相當夠用了。

---

其次，是提供範例，讓 AI 知道我們的期望的具體樣貌。像是神燈許願的故事，如果許的願望不夠精準，神燈精靈也會「模糊」的滿足願望。像是「我想要變有錢」，神燈精靈可能只會給你 100 萬，但如果你說「我想要變成有錢人」，神燈精靈會給你 1000 萬。

如果願望更為精準，許一個「我想要變成巴菲特那樣有錢，且擁有能夠一輩子花不完的錢，而且錢幣不會隨時代貶值，並且不佔用空間。」，神燈精靈可能給你的是一張「沒有額度上限的信用卡」（超級魔法小卡），讓你一輩子「不受額度」限制可以「無限刷卡」，且「永久有效」。


有點扯遠了，舉以上這個「警世」小故事的範例，目的是要說明，如果我們的期望不夠精準，AI 可能會給出雖可以接受，但「不盡完美」的結果，這時候我們需要提供更精準的期望，讓 AI 知道我們的期望的具體樣貌。

提供 AI 範例的方式可以有好幾種，像是以下三種：

- 提供具體的範例：提供清楚且具體的範例，讓 AI 知道我們的期望的具體樣貌。
- 提供抽象的範例：提供抽象的概念範例，描述期望應該要有的樣子，但沒有太多具體的細節。
- 提供反例：提供反例，讓 AI 知道我們「不希望的反面樣貌」。

接著，我們來看看這三種方式究竟是該如何讓 Prompt 更精準。

首先，是提供具體的範例。承襲上一節的範例，我們可以提供以下 Prompt：
```
請幫我設計一個 React 的表單，包含以下規格：

  1. 設計表單結構
    請設計成類似如下格式，將每個欄位設計成一個 FormItem，並且每個欄位需要包含 FormLabel、FormControl 和 FormMessage，可以使用 Shadcn 的 UI 元件：
    ```
    <Form>
      <FormItem>
        <FormLabel>使用者名稱</FormLabel>
        <FormControl>
          <Input placeholder="請輸入使用者名稱" />
        </FormControl>
        <FormMessage />
        //...
      </FormItem>
    </Form>
    ```
  2. 表單規格
    - 以 React Hook Form 實作
    - 元件使用 Shadcn 的 UI 元件
    - 表單需要包含以下欄位：
      - 使用者名稱：必填，8 ~ 16 個字
      - 使用者密碼：必填，8 ~ 16 個字
      - 使用者信箱：必填，10 個字，驗證格式為 email

  3. 技術文件
    - 以 Markdown 格式撰寫
    - 文件範例如下
    ```
    # 使用者註冊表單技術文件

    ## 表單技術結構

    ### 欄位驗證規則

    ### 測試案例

    ### 使用情境
    ```
```

產出的 Prompt 如下所示意，可以看到 Prompt 相對於以上的「清單」 Prompt ，在產出的「結構」上更為可控，但細節上比較不全。不過這想想也合理，畢竟根本沒有提供那麼多的細節，AI 怎麼可能產出那麼多細節的結果呢？

特別是「技術文件」的產出，可以很明顯的感受到，比起「清單」 Prompt 的結果，更為完整，且更符合我們的期望。有依照我們提供的「模板」範例，依照需求乖乖地產出完整的技術文件。

```
以下是一個符合您需求的 React 表單設計，包含表單結構、技術文件以及相關的驗證規則。我將使用 React Hook Form 和 Shadcn 的 UI 元件來實現。

---

### 1. 表單結構
```tsx
import { useForm } from "react-hook-form";
import { Button } from "@/components/ui/button";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Input } from "@/components/ui/input";

export function RegisterForm() {
  const form = useForm({
    defaultValues: {
      username: "",
      password: "",
      email: "",
    },
  });

  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <Form {...form}>
      <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-4">
        //...
        <FormField
          control={form.control}
          name="email"
          rules={{
            required: "電子郵件為必填",
            maxLength: {
              value: 10,
              message: "電子郵件不能超過10個字",
            },
            pattern: {
              value: /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i,
              message: "請輸入有效的電子郵件格式",
            },
          }}
          render={({ field }) => (
            <FormItem>
              <FormLabel>使用者信箱</FormLabel>
              <FormControl>
                <Input type="email" placeholder="請輸入電子郵件" {...field} />
              </FormControl>
              <FormMessage />
            </FormItem>
          )}
        />

        <Button type="submit">註冊</Button>
      </form>
    </Form>
  );
}
```

---

### 2. 技術文件
```markdown
# 使用者註冊表單技術文件

## 表單技術結構
- **框架**：React + React Hook Form
- **UI 元件庫**：Shadcn

### 欄位驗證規則
1. **使用者名稱**：
   - 必填。
   - 長度限制：8 ~ 16 個字。
2. **使用者密碼**：
   - 必填。
   - 長度限制：8 ~ 16 個字。
3. **使用者信箱**：
   - 必填。
   - 長度限制：最多 10 個字。
   - 格式驗證：必須符合電子郵件格式。

### 測試案例
- 測試所有欄位的必填驗證。
- 測試欄位的長度限制。
- 測試電子郵件的格式驗證。
- 測試表單提交功能。

### 使用情境
- 適用於需要使用者註冊功能的前端應用。
- 可用於原型開發或正式產品。
```

---

### 3. 測試程式碼
```tsx
import { render, screen, fireEvent } from "@testing-library/react";
import { RegisterForm } from "./RegisterForm";

describe("RegisterForm", () => {
  it("should validate username field", async () => {
    render(<RegisterForm />);
    const usernameInput = screen.getByPlaceholderText("請輸入使用者名稱");

    // 測試必填
    fireEvent.blur(usernameInput);
    expect(await screen.findByText("使用者名稱為必填")).toBeInTheDocument();

    // 測試長度限制
    fireEvent.change(usernameInput, { target: { value: "a".repeat(7) } });
    fireEvent.blur(usernameInput);
    expect(await screen.findByText("使用者名稱需至少8個字")).toBeInTheDocument();

    fireEvent.change(usernameInput, { target: { value: "a".repeat(17) } });
    fireEvent.blur(usernameInput);
    expect(await screen.findByText("使用者名稱不能超過16個字")).toBeInTheDocument();
  });

  // 其他欄位的測試案例可以依此類推
});
```

```

接下來，先講一下「反例」。正面例子是利用「正向規範拘束」，請求 AI 幫我們照著期望「照樣照句」產出結果。

反例則是利用「負向規範拘束」，請求 AI 幫我們避免產出某些內容。

像是以下 Prompt 是請求 AI 幫我們避免產出某些內容，因為我們有先前的經驗，知道某些內容是不想要產出的：
```
請幫我設計一個 React 的表單，包含以下規格：

1. 表單結構
- 需要有 使用者名稱、使用者密碼、使用者信箱 三個欄位。都是必填，且需要有驗證規則。
  - 使用者名稱：必填，8 ~ 16 個字
  - 使用者密碼：必填，8 ~ 16 個字
  - 使用者信箱：必填，10 個字，驗證格式為 email
- 不要使用 原生 HTML 的 input, button, form 元件
- 不要寫註解
- 在表單的送出觸發中，不要寫 console.log

2. 技術文件
- 不要有英文說明
- 寫最精簡即可

3. 測試程式碼
- 不用寫錯誤案例
- 不用寫邊界條件
```

以下節錄部分 Prompt 產出的結果，可以看到之前都會在 onSubmit 中寫 console.log，但現在都沒有，透過負向規範拘束，我們成功避免產出特定不希望產出的結果：
```
### 1. 表單結構
```tsx
import { useForm } from "react-hook-form";
import { Button } from "@/components/ui/button";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Input } from "@/components/ui/input";

export function RegisterForm() {
  const form = useForm({
    defaultValues: {
      username: "",
      password: "",
      email: "",
    },
  });

  const onSubmit = (data) => {
    // 表單提交邏輯
  };

  return (
    <Form {...form}>
      //...
    </Form>
  );
}
```
//... 省略技術文件部分產出

### 3. 測試程式碼
```tsx
import { render, screen, fireEvent } from "@testing-library/react";
import { RegisterForm } from "./RegisterForm";

describe("RegisterForm", () => {
  it("should submit the form if validation passes", async () => {
    render(<RegisterForm />);
    const usernameInput = screen.getByPlaceholderText("請輸入使用者名稱");
    const passwordInput = screen.getByPlaceholderText("請輸入密碼");
    const emailInput = screen.getByPlaceholderText("請輸入電子郵件");
    const submitButton = screen.getByText("註冊");

    fireEvent.change(usernameInput, { target: { value: "validuser" } });
    fireEvent.change(passwordInput, { target: { value: "validpassword" } });
    fireEvent.change(emailInput, { target: { value: "valid@email.com" } });
    fireEvent.click(submitButton);
  });
});
```

最後，是抽象的範例。像是以下 Prompt 是請求 AI 幫我們產出抽象的概念範例，描述期望應該要有的樣子，但沒有太多具體的細節。

```
請幫我設計一個 React 的表單：

1. 表單結構
- 需要有 使用者名稱、使用者密碼、使用者信箱 三個欄位。都是必填，且需要有驗證規則。
- 驗證規格可以按照大多數的表單驗證規則，像是長度限制、格式驗證等。

2. 技術文件
- 以常見的技術文件格式撰寫
- 文件結構優良，至少要有三個段落，分別解說表單結構、功能以及使用情境等。

3. 測試程式碼
- 以常見的測試程式碼格式撰寫
- 測試程式碼至少要有三個案例，分別測試表單結構、功能以及使用情境等。
```

產出的 Prompt 如下所示意，透過抽象的範例，讓 AI 可以更自由地發揮，藉由其「大型語言模型」的特性，產出「更為大眾」的結果。讓我們不必拘泥於特定的框架或技術，而是「更像是客戶」所想要的需求那般描述需求，而非指定太多的規格細節，反而讓 AI 無法發揮。

這樣的好處是，不必一開始就想好太多特定規格細節，而是先產個 6 ~ 8 成左右，根據產出結果「收斂」，做逐步調整。上述具體案例，產出結果大概 7 ~ 9 成可以直接使用，剩下 1 ~ 3 成再細微調整就好，但提供具體案例的前期準備比較耗時，所以可以先產出抽象的範例，再逐步收斂。

尤其像是測試案例，雖然案例不夠完整（也不見得真的有測試足夠精準），但可以像這樣先產出大略的結果，將測試的「框架」先建立起來。

```

以下是一個符合您需求的 React 表單設計，包含表單結構、技術文件以及測試程式碼。我將使用 React Hook Form 來實現表單驗證，並以 Markdown 格式撰寫技術文件。

---

### 1. 表單結構
```tsx
import { useForm } from "react-hook-form";
import { Button } from "@/components/ui/button";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Input } from "@/components/ui/input";

export function RegisterForm() {
  const form = useForm({
    defaultValues: {
      username: "",
      password: "",
      email: "",
    },
  });

  const onSubmit = (data) => {
    console.log(data);
  };

  return (
    <Form {...form}>
      <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-4">
        //... 省略

        <FormField
          control={form.control}
          name="password"
          rules={{
            required: "密碼為必填",
            minLength: {
              value: 6,
              message: "密碼長度需至少6個字",
            },
            maxLength: {
              value: 16,
              message: "密碼長度不能超過16個字",
            },
          }}
          render={({ field }) => (
            <FormItem>
              <FormLabel>使用者密碼</FormLabel>
              <FormControl>
                <Input type="password" placeholder="請輸入密碼" {...field} />
              </FormControl>
              <FormMessage />
            </FormItem>
          )}
        />

        //... 省略
      </form>
    </Form>
  );
}
```

---

### 2. 技術文件
```markdown
# 使用者註冊表單技術文件

## 表單結構
- **框架**：React + React Hook Form
- **UI 元件庫**：Shadcn

### 欄位驗證規則
1. **使用者名稱**：
   - 必填。
   - 長度限制：3 ~ 20 個字。
2. **使用者密碼**：
   - 必填。
   - 長度限制：6 ~ 16 個字。
3. **使用者信箱**：
   - 必填。
   - 格式驗證：必須符合電子郵件格式。

## 功能
- 表單提交時會驗證所有欄位是否符合規則。
- 若驗證失敗，會顯示對應的錯誤訊息。
- 若驗證通過，表單會提交資料。

## 使用情境
- 適用於需要使用者註冊功能的前端應用。
- 可用於原型開發或正式產品。
```

---

### 3. 測試程式碼
```tsx
import { render, screen, fireEvent } from "@testing-library/react";
import { RegisterForm } from "./RegisterForm";

describe("RegisterForm", () => {
  it("should validate username field", async () => {
    //... 省略
  });

  it("should validate email field", async () => {
    //... 省略
  });

  it("should submit the form if validation passes", async () => {
    //... 省略
  });
});
```


---


最後，以 SMART 原則來為 Prompt 品質設計做個總結。

SMART 原則分別是：
- Specific: 具體。
- Measurable: 可衡量。
- Achievable: 可達成。
- Relevant: 相關。
- Time-bound: 時限性。

1. 具體：對應到上面提到的清單以及「具體」範例，藉由提供完整且具體的範例，讓 AI 可以更清楚地理解我們的期望。「具體來說」，有想到什麼，就給什麼，越清楚詳細越好。AI 通靈能力蠻強的，可以多給一些提示來規範拘束，讓 AI 可以更清楚地理解我們期望的「關鍵字」。

比方說，在請 AI 提供程式碼時，在選用技術方面，可以這樣提示：
- 「請以 TypeScript, React, React Hook Form, Shadcn 為基礎」
- 「請以 Tailwind CSS, SASS 為樣式之套件基礎」

又或者比較「抽象」一點的，假設想要改善網站的 SEO，可以這樣提示：
- 「請以 SEO 最佳化為基礎，幫我檢查網站目前有哪些問題」
- 「請以現有常見之 SEO 追蹤工具，幫我檢查網站還有哪些可以改善的地方，我希望可以在 Meta 平台、Google 平台、Bing 平台等，增加用戶流量」


2. 可衡量，是指目標具有量化標準，讓你能追蹤進度並評估成功與否。加入「數字或指標」來衡量成果很有幫助，在技術開發中，「可衡量」意味著設定具體的量化指標來評估成效。包括但不限於：效能指標、程式碼品質、使用者體驗等。像是希望效能指標提升，從 500ms 提升至 200ms，這樣的量化指標，可以讓 AI 提供更為精準的建議。

這些量化目標讓團隊能明確知道「完成」的標準，客觀評估改進效果，根據數據做決策。 例如：「將 API 響應時間從 500ms 優化至 200ms 內」比「讓 API 變快」更具可操作性。量化目標也方便用工具（如 Lighthouse、WebPageTest）追蹤進度。

以下是提示的範例：
- 「請以 SEO 最佳化為基礎，幫我從 Lighthouse 分數的 60 分提升到 80 分，以網站效能、圖片壓縮、網站速度、網站安全等以上至少四項指標為基礎。提供我優化網站之具體建議。」
- 「請幫我優化這段 React 元件渲染效能，目標是將重新渲染次數從目前的平均 5 次降低到 2 次以下，並使用 React Profiler 提供的數據作為衡量基準。具體需要分析元件不必要的重新渲染原因，並提供 memoization 或 useCallback 的實作建議。」


3. 可達成：是指目標具有可達成性，必須是「現實可行的」。在我們開發中，這個算是比較難量化評估的一點，也是難以一概而論。這意味著設定的目標應考慮團隊能力、資源限制和技術可行性，蠻仰賴團隊的經驗以及專案的規模的評估。例如，要求初學者在一天內掌握 React 高級概念就不切實際，但兩週內完成基礎元件開發則是合理目標。好的目標應能分解為具體任務，並有明確的驗收標準。
因此，想要從 AI 那邊得到有用的建議時，要先審慎評估可行性，避免提供不切實際的方案（如要求小型團隊短期內實現大規模分散式系統）。設定可達成目標能保持團隊動力並確保專案持續進展。

以下是提示的範例：
- 「在 3 個月內將網站核心網頁指標 (Core Web Vitals) 中的 LCP (最大內容繪製) 從目前的 4.2 秒改善至 2.5 秒內，透過圖片優化、延遲載入和非關鍵資源的異步處理。請幫我提供具體的優化建議與時程規劃。」
- 「在 2 週內完成基本的 SEO 優化，包括：1) 為所有頁面添加完整的 meta 標籤 2) 確保所有圖片都有 alt 屬性 3) 建立完整的 sitemap.xml 和 robots.txt 文件。請幫我提供具體的優化建議與時程規劃。」
以上提供了在一段時間內達成的期望，AI 可以根據此期望，提供更為可靠的精準建議。否則像是「我想要在一天之內，讓網站的客戶人流從每天 0 訪客，提升至平均每天 100 萬訪客。給我建議」，AI 還是會很「認份」給出回覆，但會認為這個目標太過遙遠，無法提供比較可靠的建議。


4. 相關性：是指目標具有相關性，必須是「符合我們期望的」。

尤其在技術開發中，相關性意味著我們設定的目標要與專案的核心需求直接掛鉤。例如優化表單驗證時，應專注於提升使用者體驗而非無關的後端效能。選擇技術方案時，需考慮團隊熟悉度與專案規模，避免引入過度複雜但不相關的解決方案。

當要求AI協助時，提供的背景資訊應與問題高度相關，例如優化React元件時，需包含現有程式碼結構而非泛泛而談效能問題。比方說以下範例

- 「請以提升使用者註冊轉換率為目標，分析目前表單流程的痛點，並提供具體優化建議。」
- 「請以改善 React 元件可維護性為目標，分析目前程式碼結構，並提供重構建議。重點關注：元件職責單一化、狀態管理集中化，以及可測試性提升。」

5. 時限性：是指目標具有明確的時間框架。
時限性是指為目標設定明確的時間框架，這在技術開發中尤為重要。合理的時程規劃能幫助團隊保持專注並有效追蹤進度。例如，設定「兩週內完成 API 重構」比「盡快完成」更具指導意義。時限性也讓 AI 能根據時間約束提供更實際的建議，如短期方案可能側重快速修復，而長期方案則考慮架構優化。同時，時間壓力也能促使團隊優先處理高價值任務，避免完美主義導致的過度優化。在設定時限時，需平衡急迫性與可行性，確保目標在期限內可達成。


- 「請在 2 天內提供 3 種不同的解決方案來優化這個資料庫查詢效能，並比較它們的優缺點。」
- 「請在 1 週內完成這個功能的原型開發，使用 Next.js 框架並整合現有的 API 端點。」


### 綜合應用 - 產出程式碼

應用以上原則，我們可以設計出更符合我們期望的 Prompt。

前後比較：
無應用原則的 Prompt：
```
請幫我實作一個 Fibonnaci 數列。
```

有應用原則的 Prompt：
```
請幫我實作一個 Fibonnaci 數列，提供我 3 個範例。

- 範例 1：使用遞迴。
- 範例 2：使用迴圈。
- 範例 3：使用記憶化。

```








### 測試與調整

