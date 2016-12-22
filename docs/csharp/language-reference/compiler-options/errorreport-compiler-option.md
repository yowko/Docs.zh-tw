---
title: "/errorreport (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/errorreport"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-errorreport compiler option [C#]"
  - "errorreport compiler option [C#]"
  - "/errorreport compiler option [C#]"
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
caps.latest.revision: 35
caps.handback.revision: 35
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /errorreport (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

這個選項提供便利的方式，讓您可以向 Microsoft 報告 C\# 編譯器內部的錯誤。  
  
> [!NOTE]
>  在 Windows Vista 和 Windows Server 2008 上，您對 Visual Studio 所做的錯誤報告設定並不會覆寫已透過 Windows 錯誤報告 \(Windows Error Reporting，WER\) 所完成的設定。  WER 設定永遠都會比 Visual Studio 錯誤報告設定優先考慮。  
  
## 語法  
  
```  
/errorreport:{ none | prompt | queue | send }  
```  
  
## Arguments  
 **none**  
 將不會收集有關內部編譯器錯誤的報告，也不會將報告傳送給 Microsoft。  
  
 **prompt**  
 提示您在收到內部編譯器錯誤時傳送報告。  當您在開發環境中編譯應用程式時，預設值會是 **prompt**。  
  
 **queue**  
 將錯誤報告排入佇列。  當您以系統管理認證登入時，您可以報告自上次登入後的任何失敗。  每三天，系統不會提示您傳送失敗報告一次以上。  當您在命令列編譯應用程式時，預設值會是 **queue**。  
  
 **send**  
 自動傳送內部編譯器錯誤報告給 Microsoft。  若要啟用這個選項，您必須先同意 Microsoft 的資料收集原則。  初次在電腦上指定 **\/errorreport:send** 時，編譯器訊息會指引您到包含 Microsoft 資料收集原則的網站上。  
  
 這個選項取決於登錄設定。  如需在登錄中設定適當值的詳細資訊，請參閱 MSDN 網站上的[如何在 Visual Studio 2008 命令列工具中開啟自動錯誤報告](http://go.microsoft.com/fwlink/?LinkID=184695)。  
  
## 備註  
 當編譯器無法處理原始程式檔時，就會產生內部編譯器錯誤 \(ICE\)。  發生 ICE 時，編譯器不會產生輸出檔，也不會產生任何有用的診斷，供您用來修正程式碼。  
  
 在舊版中，當您接到 ICE 訊息時，希望您盡可能聯繫 Microsoft 產品支援服務部門，將問題報告給他們。  使用 **\/errorreport** 時，您可以將 ICE 資訊提供給 Visual C\# 團隊。  您的錯誤報告可以協助改善將來的編譯器版本。  
  
 使用者是否能夠傳送報告，完全是依電腦和使用者的原則權限而定。  
  
 如需錯誤偵錯工具的詳細資訊，請參閱 [Dr. Watson 對 Windows \(Drwtsn32.exe\) 工具的描述](http://go.microsoft.com/fwlink/?LinkId=147286)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性**\] 頁面。  如需詳細資訊，請參閱[專案設計工具、建置頁 \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp)。  
  
2.  按一下 \[**建置**\] 屬性頁。  
  
3.  按一下 \[進階\] 按鈕。  
  
4.  修改 \[**報告內部編譯器錯誤**\] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>。  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)