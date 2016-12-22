---
title: "互通性 (C# 程式設計手冊) | Microsoft Docs"
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
  - "COM Interop"
  - "互通性"
  - "平台叫用, 使用 C# 存取 API"
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 互通性 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

互通性可讓您保留並運用在 Unmanaged 程式碼中的現有投資。  在 Common Language Runtime \(CLR\) 控制下所執行的程式碼稱為「*Managed 程式碼*」\(Managed Code\)，而在 CLR 外部執行的程式碼則稱為「*Unmanaged 程式碼*」\(Unmanaged Code\)。  例如，COM、COM\+、C\+\+ 元件、ActiveX 元件和 Microsoft Win32 API 都是 Unmanaged 程式碼。  
  
 透過平台叫用服務、<xref:System.Runtime.InteropServices> 命名空間、C\+\+ 互通性 \(Interoperability\) 和 COM 互通性 \(COM interop\)，[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 可以與 Unmanaged 程式碼互通。  
  
## 本章節內容  
 [互通性概觀](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 說明可讓 C\# Managed 程式碼和 Unmanaged 程式碼互通的方法。  
  
 [如何：使用 Visual C\#  功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 描述在 Visual C\# 2010 中引進以利於 Office 程式設計的功能。  
  
 [如何：在 COM Interop 程式設計中使用索引的屬性](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 描述如何使用索引的屬性來存取具有參數的 COM 屬性。  
  
 [如何：使用平台叫用播放 WAV 檔](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 說明如何在 Windows 作業系統上使用平台叫用服務播放 .wav 音效檔。  
  
 [逐步解說：Office 程式設計](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 示範如何建立 Excel 活頁簿和包含連結至活頁簿的 Word 文件。  
  
 [範例 COM 類別](../../../csharp/programming-guide/interop/example-com-class.md)  
 示範如何將 C\# 類別公開 \(Expose\) 為 COM 物件。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=fullName>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [逐步解說：Office 程式設計](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)