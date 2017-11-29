---
title: "如何：判斷安裝的 WPF 版本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60f2dd65702a5dfcff4cbafa97e5a48080b8e5be
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>如何：判斷安裝的 WPF 版本
目前安裝的版本的版本號碼[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]位於**登錄**。  
  
 若要尋找版本號碼：  
  
1.  在 [ **開始** ] 功能表中按一下 [ **執行**]。  
  
2.  在**開啟**，型別**regedit.exe**。  
  
3.  開啟下列機碼：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版本號碼儲存在**版本**值。
