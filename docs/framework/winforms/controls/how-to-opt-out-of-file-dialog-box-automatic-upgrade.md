---
title: 如何：選擇不自動升級檔案對話方塊
ms.date: 03/30/2017
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
ms.openlocfilehash: 154953680426f98a9506feb0b8f4de25c873b795
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959678"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="a9c44-102">如何：選擇不自動升級檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="a9c44-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="a9c44-103">當應用程式中使用 <xref:System.Windows.Forms.OpenFileDialog> 和 <xref:System.Windows.Forms.SaveFileDialog> 類別時，其外觀和行為取決於應用程式執行所在的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="a9c44-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="a9c44-104">在 Windows Vista 上顯示在 .NET Framework 2.0 或更早版本上建立的應用程式時，<xref:System.Windows.Forms.OpenFileDialog> 和 <xref:System.Windows.Forms.SaveFileDialog> 會自動顯示 Windows Vista 的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="a9c44-104">When an application that was created on the .NET Framework 2.0 or earlier is displayed on Windows Vista, <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the Windows Vista appearance and behavior.</span></span> <span data-ttu-id="a9c44-105">從 .NET Framework 3.0 開始，您可以退出宣告自動升級，以 Windows XP 樣式的外觀和行為來顯示 <xref:System.Windows.Forms.OpenFileDialog> 和 <xref:System.Windows.Forms.SaveFileDialog>。</span><span class="sxs-lookup"><span data-stu-id="a9c44-105">Starting in the .NET Framework 3.0, you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a Windows XP-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="a9c44-106">選擇不自動升級檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="a9c44-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1. <span data-ttu-id="a9c44-107">將 <xref:System.Windows.Forms.OpenFileDialog> 或 <xref:System.Windows.Forms.SaveFileDialog> 的 <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> 屬性設定為 [`false`]，才會顯示對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a9c44-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c44-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9c44-108">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
