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
ms.workload: dotnet
ms.openlocfilehash: b785b9da22aa6f17c14b85263b94fb70fbef5f7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="81e3b-102">如何：選擇不自動升級檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="81e3b-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="81e3b-103">當<xref:System.Windows.Forms.OpenFileDialog>和<xref:System.Windows.Forms.SaveFileDialog>類別用在應用程式，其外觀和行為取決於 Windows 執行應用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="81e3b-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="81e3b-104">在建立應用程式時[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]或前面會顯示在[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]，<xref:System.Windows.Forms.OpenFileDialog>和<xref:System.Windows.Forms.SaveFileDialog>會自動顯示與[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="81e3b-104">When an application that was created on the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] or earlier is displayed on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] appearance and behavior.</span></span> <span data-ttu-id="81e3b-105">從開始[!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)]，您可以選擇不自動升級，以顯示<xref:System.Windows.Forms.OpenFileDialog>和<xref:System.Windows.Forms.SaveFileDialog>與[!INCLUDE[winxp](../../../../includes/winxp-md.md)]-樣式外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="81e3b-105">Starting in the [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="81e3b-106">選擇不自動升級檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="81e3b-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1.  <span data-ttu-id="81e3b-107">設定<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>屬性<xref:System.Windows.Forms.OpenFileDialog>或<xref:System.Windows.Forms.SaveFileDialog>至`false`對話方塊顯示之前。</span><span class="sxs-lookup"><span data-stu-id="81e3b-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e3b-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="81e3b-108">See Also</span></span>  
 <xref:System.Windows.Forms.FileDialog>
