---
title: "如何：判斷安裝的 WPF 版本 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "版本, 尋找"
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# 如何：判斷安裝的 WPF 版本
目前安裝之 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 版本的版本號碼位於「登錄」中。  
  
 若要找出版本號碼：  
  
1.  在 \[**開始**\] 功能表上，按一下 \[**執行**\]。  
  
2.  在 \[開啟\] 中輸入 **regedit.exe**。  
  
3.  開啟下列機碼：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版本號碼儲存在 \[版本\] 值中。