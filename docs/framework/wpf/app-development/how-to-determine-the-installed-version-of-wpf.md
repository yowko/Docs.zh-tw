---
title: HOW TO：判斷安裝的 WPF 版本
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: ffbd9a4c7f66dff9c8773dff4259551e20aa963d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052452"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>HOW TO：判斷安裝的 WPF 版本
目前安裝版本的版本號碼[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]位於**登錄**。  
  
 若要尋找版本號碼：  
  
1. 在 [ **開始** ] 功能表中按一下 [ **執行**]。  
  
2. 在 **開放**，型別**regedit.exe**。  
  
3. 開啟下列機碼：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版本號碼儲存在**版本**值。
