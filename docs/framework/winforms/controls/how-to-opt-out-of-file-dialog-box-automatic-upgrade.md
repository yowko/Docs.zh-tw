---
title: "如何：選擇不自動升級檔案對話方塊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01be9e29c00f39125c8ee645242e986fac178ba2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>如何：選擇不自動升級檔案對話方塊
當<xref:System.Windows.Forms.OpenFileDialog>和<xref:System.Windows.Forms.SaveFileDialog>類別用在應用程式，其外觀和行為取決於 Windows 執行應用程式的版本。 在建立應用程式時[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]或前面會顯示在[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]，<xref:System.Windows.Forms.OpenFileDialog>和<xref:System.Windows.Forms.SaveFileDialog>會自動顯示與[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]外觀和行為。 從開始[!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)]，您可以選擇不自動升級，以顯示<xref:System.Windows.Forms.OpenFileDialog>和<xref:System.Windows.Forms.SaveFileDialog>與[!INCLUDE[winxp](../../../../includes/winxp-md.md)]-樣式外觀和行為。  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>選擇不自動升級檔案對話方塊  
  
1.  設定<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>屬性<xref:System.Windows.Forms.OpenFileDialog>或<xref:System.Windows.Forms.SaveFileDialog>至`false`對話方塊顯示之前。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.FileDialog>
