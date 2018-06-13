---
title: 如何：判斷安裝的 WPF 版本
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: c59fa0d0a4d94c6e6a2ab72a4cd7a3c066649fb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545847"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>如何：判斷安裝的 WPF 版本
目前安裝的版本的版本號碼[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]位於**登錄**。  
  
 若要尋找版本號碼：  
  
1.  在 [ **開始** ] 功能表中按一下 [ **執行**]。  
  
2.  在**開啟**，型別**regedit.exe**。  
  
3.  開啟下列機碼：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版本號碼儲存在**版本**值。
