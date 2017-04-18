---
title: "使用 COM Interop 封送處理資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM Interop, 資料封送處理"
  - "封送處理資料, COM Interop"
ms.assetid: 0bcdd7bf-5026-43eb-b08b-f03f90db9df9
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 使用 COM Interop 封送處理資料
COM Interop 同時提供使用來自 Managed 程式碼之 COM 物件的支援和公開 Managed 物件給 COM 的支援。  廣泛支援封送處理資料至 COM 或對來自 COM 的資料封送處理，幾乎一律會提供正確的封送處理行為。  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 包含下列的 COM Interop 工具：  
  
-   [類型程式庫匯入工具 \(Tlbimp.exe\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)，這會將 COM 類型程式庫轉換成 Interop 組件。  從這個組件中，Interop 封送處理服務會產生包裝函式，在 Managed 和 Unmanaged 記憶體之間執行資料封送處理。  
  
-   [類型程式庫匯出工具 \(Tlbexp.exe\)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)，這會從組件產生 COM 類型程式庫，並產生在方法呼叫期間執行封送處理的包裝函式。  
  
 本節描述當您可以 \(或必須\) 提供具有其他類型資訊的封送處理器時，自訂 Interop 包裝函式的程序。  
  
## 在本節中  
 [COM 資料類型](http://msdn.microsoft.com/zh-tw/f93ae35d-a416-4218-8700-c8218cc90061)  
 提供對應的 Managed 和 Unmanaged 資料類型。  
  
 [自訂 COM 可呼叫包裝函式](http://msdn.microsoft.com/zh-tw/825177d3-4b2c-4723-82be-ce6ca2c34ace)  
 描述如何在設計階段使用 **MarshalAsAttribute** 屬性明確封送處理資料類型。  
  
 [自訂執行階段可呼叫包裝函式](http://msdn.microsoft.com/zh-tw/4652beaf-77d0-4f37-9687-ca193288c0be)  
 描述如何調整 Interop 組件中的類型封送處理行為，以及描述如何以手動方式定義 COM 類型。  
  
 [如何：將 Managed 程式碼 DCOM 移轉至 WCF](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 描述如何將 Managed 的 DCOM 程式碼移轉至 WCF 的最安全解決方案。  
  
## 相關章節  
 [Advanced COM Interoperability](http://msdn.microsoft.com/zh-tw/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 提供有關將 COM 元件納入 .NET Framework 應用程式的詳細資訊連結。  
  
 [Assembly to Type Library Conversion Summary](http://msdn.microsoft.com/zh-tw/3a37eefb-a76c-4000-9080-7dbbf66a4896)  
 描述組件至類型程式庫匯出轉換的程序。  
  
 [Type Library to Assembly Conversion Summary](http://msdn.microsoft.com/zh-tw/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 描述類型程式庫至組件匯入轉換的程序。  
  
 [Interoperating Using Generic Types](http://msdn.microsoft.com/zh-tw/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 描述使用泛型類型來取得 COM 互通性時所支援的動作。