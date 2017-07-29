---
title: "如何：檢視全域組件快取的內容 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "組件 [.NET Framework], 全域組件快取"
  - "GAC (全域組件快取), 檢視內容"
  - "Gacutil.exe"
  - "全域組件快取工具"
  - "全域組件快取, 檢視內容"
  - "全域組件快取中的組件清單"
  - "強式名稱組件, 全域組件快取"
  - "檢視全域組件快取中的組件"
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：檢視全域組件快取的內容
您可以使用[全域組件快取工具 \(Gacutil.exe\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 來檢視全域組件快取的內容。  
  
### 若要檢視全域組件快取中的組件清單  
  
1.  在 [Visual Studio 命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)輸入下列命令：  
  
     **gacutil \-l**   
     \-或\-               
     **gacutil \/l**  
  
 在舊版 .NET Framework 中，[Shfusion.dll](http://msdn.microsoft.com/zh-tw/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows Shell Extension 可讓您在 \[檔案總管\] 中檢視全域組件快取。  從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]開始，Shfusion.dll 已過時。  
  
## 請參閱  
 [使用組件和全域組件快取](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)