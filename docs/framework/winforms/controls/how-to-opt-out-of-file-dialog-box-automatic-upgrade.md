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
ms.openlocfilehash: 0753873ac37f26d6503397290ef4603702737a86
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170620"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>如何：選擇不自動升級檔案對話方塊
當<xref:System.Windows.Forms.OpenFileDialog>和<xref:System.Windows.Forms.SaveFileDialog>類別用在應用程式，其外觀和行為取決於 Windows 執行應用程式的版本。 當.NET Framework 2.0 或更早版本所建立的應用程式會顯示在[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]，<xref:System.Windows.Forms.OpenFileDialog>並<xref:System.Windows.Forms.SaveFileDialog>會自動顯示具有[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]外觀和行為。 從.NET Framework 3.0 開始，您可以選擇不自動升級，以顯示<xref:System.Windows.Forms.OpenFileDialog>並<xref:System.Windows.Forms.SaveFileDialog>使用[!INCLUDE[winxp](../../../../includes/winxp-md.md)]-樣式外觀和行為。  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>選擇不自動升級檔案對話方塊  
  
1. 設定<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>的屬性<xref:System.Windows.Forms.OpenFileDialog>或是<xref:System.Windows.Forms.SaveFileDialog>到`false`顯示對話方塊之前。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.FileDialog>
