---
title: 部署參考 Power Packs 控制項 (Visual Studio) 的應用程式
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2a9562acf05cd27eed7bc1ad963845af9a7ca5f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>部署參考 Power Packs 控制項 (Visual Studio) 的應用程式
如果您想要部署參考 Power Packs 控制項的應用程式 (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>， <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>， <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>，或<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>)，必須在目的地電腦上安裝的控制項。  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>安裝 Power Packs 控制項的必要元件  
 若要順利部署應用程式，您也必須部署應用程式參考的所有元件。 安裝必要條件元件的程序稱為 *「啟動載入」*(Bootstrapping)。  
  
 當[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]安裝開發電腦上，啟動載入器套件加入至 Power Pack[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]啟動載入器目錄。 接著，當您遵循程序加入 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 或 Windows Installer 部署的必要條件時，就可以使用這個套件。  
  
 預設會從安裝套件所在的相同位置來部署啟動載入的元件。 或者，您也可以視需要選擇從使用者可下載元件的 URL 或檔案共用位置來部署元件。  
  
> [!NOTE]
>  若要安裝啟動載入的元件，使用者可能需要該電腦的系統管理或類似的使用者權限。 若為 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 應用程式，則不論應用程式所指定的安全性層級為何，使用者都需要系統管理權限才能安裝應用程式。 安裝應用程式之後，使用者不需要系統管理權限，即可執行應用程式。  
  
 在安裝期間，將會提示使用者如果它們不會出現在目的地電腦上安裝 Power Packs 控制項。  
  
 啟動載入或者，您可以使用電子軟體發佈系統，例如 Microsoft Systems Management Server 預先部署 Power Packs 控制項。  
  
## <a name="see-also"></a>請參閱  
 [如何：使用 ClickOnce 應用程式安裝必要條件](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Visual Basic Power Packs 控制項](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
