---
title: 部署參考 Power Packs 控制項 (Visual Studio) 的應用程式
ms.date: 07/20/2015
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
ms.openlocfilehash: bd235bc0b4a7f9978333931ae1dce012c0950374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>部署參考 Power Packs 控制項 (Visual Studio) 的應用程式
如果您想要部署參考 Power Packs 控制項的應用程式 (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>， <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>， <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>，或<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>)，必須在目的地電腦上安裝的控制項。  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>安裝 Power Packs 控制項的必要元件  
 若要順利部署應用程式，您也必須部署應用程式參考的所有元件。 安裝必要條件元件的程序稱為 *「啟動載入」*(Bootstrapping)。  
  
 在開發電腦上安裝 Visual Studio 時，Power Pack 啟動載入器套件加入到 Visual Studio 啟動載入器目錄。 接著，當您遵循程序加入 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 或 Windows Installer 部署的必要條件時，就可以使用這個套件。  
  
 預設會從安裝套件所在的相同位置來部署啟動載入的元件。 或者，您也可以視需要選擇從使用者可下載元件的 URL 或檔案共用位置來部署元件。  
  
> [!NOTE]
>  若要安裝啟動載入的元件，使用者可能需要該電腦的系統管理或類似的使用者權限。 若為 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 應用程式，則不論應用程式所指定的安全性層級為何，使用者都需要系統管理權限才能安裝應用程式。 安裝應用程式之後，使用者不需要系統管理權限，即可執行應用程式。  
  
 在安裝期間，將會提示使用者如果它們不會出現在目的地電腦上安裝 Power Packs 控制項。  
  
 啟動載入或者，您可以使用電子軟體發佈系統，例如 Microsoft Systems Management Server 預先部署 Power Packs 控制項。  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用 ClickOnce 應用程式安裝必要條件](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Visual Basic Power Packs 控制項](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
