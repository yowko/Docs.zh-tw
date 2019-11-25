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
ms.openlocfilehash: bbde260cc7f05226c9b06325b45708e1cde3cf8c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976888"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>如何：選擇不自動升級檔案對話方塊
當應用程式中使用 <xref:System.Windows.Forms.OpenFileDialog> 和 <xref:System.Windows.Forms.SaveFileDialog> 類別時，其外觀和行為取決於應用程式執行所在的 Windows 版本。 在 Windows Vista 上顯示在 .NET Framework 2.0 或更早版本上建立的應用程式時，<xref:System.Windows.Forms.OpenFileDialog> 和 <xref:System.Windows.Forms.SaveFileDialog> 會自動顯示 Windows Vista 的外觀和行為。 從 .NET Framework 3.0 開始，您可以退出宣告自動升級，以 [!INCLUDE[winxp](../../../../includes/winxp-md.md)]樣式的外觀和行為來顯示 <xref:System.Windows.Forms.OpenFileDialog> 和 <xref:System.Windows.Forms.SaveFileDialog>。  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>選擇不自動升級檔案對話方塊  
  
1. 將 <xref:System.Windows.Forms.OpenFileDialog> 或 <xref:System.Windows.Forms.SaveFileDialog> 的 <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> 屬性設定為 [`false`]，才會顯示對話方塊。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.FileDialog>
