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
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="bcaf9-102">HOW TO：判斷安裝的 WPF 版本</span><span class="sxs-lookup"><span data-stu-id="bcaf9-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="bcaf9-103">目前安裝版本的版本號碼[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]位於**登錄**。</span><span class="sxs-lookup"><span data-stu-id="bcaf9-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="bcaf9-104">若要尋找版本號碼：</span><span class="sxs-lookup"><span data-stu-id="bcaf9-104">To find the version number:</span></span>  
  
1. <span data-ttu-id="bcaf9-105">在 [ **開始** ] 功能表中按一下 [ **執行**]。</span><span class="sxs-lookup"><span data-stu-id="bcaf9-105">On the **Start** menu, click **Run**.</span></span>  
  
2. <span data-ttu-id="bcaf9-106">在 **開放**，型別**regedit.exe**。</span><span class="sxs-lookup"><span data-stu-id="bcaf9-106">In **Open**, type **regedit.exe**.</span></span>  
  
3. <span data-ttu-id="bcaf9-107">開啟下列機碼：</span><span class="sxs-lookup"><span data-stu-id="bcaf9-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="bcaf9-108">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]版本號碼儲存在**版本**值。</span><span class="sxs-lookup"><span data-stu-id="bcaf9-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
