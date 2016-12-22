---
title: "互通性概觀 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 互通性"
  - "C++ Interop"
  - "COM Interop"
  - "互通性, 關於互通性"
  - "平台叫用"
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: 43
caps.handback.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 互通性概觀 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在本主題中，將說明可啟用 C\# Managed 程式碼和 Unmanaged 程式碼間互通性 \(Interoperability\) 的方法。  
  
## 平台叫用  
 「*平台叫用*」\(Platform Invoke\) 是一項服務，它可以讓 Managed 程式碼呼叫以動態連結程式庫 \(DLL\) 實作的 Unmanaged 函式 \(例如，Microsoft Win32 API 中的函式\)。  它會找出並叫用匯出的函式，並且依需要封送處理它的引數 \(整數、字串、陣列、結構等\) 跨越互通界限。  
  
 如需詳細資訊，請參閱 [使用 Unmanaged DLL 函式](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md)和 [如何：使用平台叫用播放 WAV 檔](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)。  
  
> [!NOTE]
>  [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md) \(CLR\) 負責管理對系統資源的存取。  呼叫 CLR 外部的 Unmanaged 程式碼時，會略過這項安全性機制，因而出現安全性風險。  例如，Unmanaged 程式碼可能會直接呼叫 Unmanaged 程式碼中的資源，而略過 CLR 安全性機制。  如需詳細資訊，請參閱 [.NET Framework 安全性](http://msdn2.microsoft.com/zh-tw/security/aa570406.aspx) \(英文\)。  
  
## C\+\+ Interop 的比較  
 您可以使用 C\+\+ Interop \(也稱為 It Just Works \(IJW\)\) 來包裝原生 \(Native\) C\+\+ 類別，讓使用 C\# 或其他 .NET Framework 語言撰寫的程式碼也可以使用此類別。  若要這麼做，您必須撰寫 C\+\+ 程式碼以包裝原生 DLL 或 COM 元件。  和其他 .NET Framework 語言不同，[!INCLUDE[vcprvc](../../../csharp/programming-guide/interop/includes/vcprvc_md.md)] 具有互通性支援，可讓 Managed 和 Unmanaged 程式碼位於相同的應用程式，甚至是同一個檔案中。  接著，您可以使用 **\/clr** 編譯器參數來產生 Managed 組件，以建置 C\+\+ 程式碼。  最後，在 C\# 專案中加入該組件的參考並使用包裝後的物件，就和您使用其他 Managed 類別一樣。  
  
## 將 COM 元件公開給 C\#  
 您可以從 C\# 專案使用 COM 元件。  一般的步驟如下：  
  
1.  找到要使用的 COM 元件，並註冊此元件。  使用 regsvr32.exe 來註冊或移除註冊 COM DLL。  
  
2.  在專案中加入 COM 元件或型別程式庫的參考。  
  
     當您加入參考時，[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 會使用[Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)，這個工具會以型別程式庫做為輸入，並輸出 .NET Framework Interop 組件。  組件 \(亦稱為執行階段可呼叫包裝函式 \(RCW\)\) 包含和包裝類別庫中的 COM 類別的 Managed 類別及介面。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 會將所產生之組件的參考加入至專案中。  
  
3.  建立類別的執行個體，這個類別是在 RCW 中定義。  這個執行個體接著會建立 COM 物件的執行個體。  
  
4.  以您在使用其他 Managed 物件時一樣的方法使用此物件。  當記憶體回收行程回收此物件時，也會從記憶體釋放 COM 物件的執行個體。  
  
 如需詳細資訊，請參閱 [將 COM 元件公開給 .NET Framework](../Topic/Exposing%20COM%20Components%20to%20the%20.NET%20Framework.md)。  
  
## 將 C\# 公開給 COM  
 COM 用戶端可以使用以正確方式公開的 C\# 型別。  公開 C\# 型別的基本步驟如下：  
  
1.  在 C\# 專案中加入 Interop 屬性 \(Attribute\)。  
  
     您可以修改 [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] 專案的屬性 \(Property\)，讓組件成為 COM 可見。  如需詳細資訊，請參閱 [組件資訊對話方塊](/visual-studio/ide/reference/assembly-information-dialog-box)。  
  
2.  產生 COM 型別程式庫，並註冊這個程式庫供 COM 使用。  
  
     您可以修改 [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] 專案屬性，以自動註冊 COM Interop 的 C\# 組件。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 使用 [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)，使用 `/tlb` 命令列參數 \(會將 Managed 組件視為輸入\) 來產生型別程式庫。  這個型別程式庫會描述組件中的 `public` 型別並加入登錄項目，使 COM 用戶端可以建立 Managed 類別。  
  
 如需詳細資訊，請參閱 [將 .NET Framework 元件公開給 COM](../Topic/Exposing%20.NET%20Framework%20Components%20to%20COM.md)和 [範例 COM 類別](../../../csharp/programming-guide/interop/example-com-class.md)。  
  
## 請參閱  
 [改善 Interop 效能](完整.嗎？LinkId%20=%2099564)   
 [介紹 COM Interop](完整.嗎？LinkId%20=%20112406)   
 [之間封送處理 Managed 和 Unmanaged 程式碼](完整.嗎？LinkId%20=%20112398)   
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Advanced COM Interoperability](http://msdn.microsoft.com/zh-tw/3ada36e5-2390-4d70-b490-6ad8de92f2fb)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)