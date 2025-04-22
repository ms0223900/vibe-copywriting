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







接下來，是 SMART 原則。



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

