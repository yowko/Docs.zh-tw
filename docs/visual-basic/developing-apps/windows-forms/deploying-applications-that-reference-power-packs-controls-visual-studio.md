---
title: "Deploying Applications That Reference Power Packs Controls (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Power Packs, deploying"
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Deploying Applications That Reference Power Packs Controls (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

如果您要部署參考 Power Packs 控制項 \(<xref:Microsoft.VisualBasic.PowerPacks.LineShape>、<xref:Microsoft.VisualBasic.PowerPacks.OvalShape>、<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> 或 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>\) 的應用程式，必須在目的電腦上安裝那些控制項。  
  
## 安裝 Power Packs 控制項做為必要條件  
 若要順利部署應用程式，您也必須部署應用程式所參考的所有元件。  安裝必要條件元件的流程又稱為「*啟動載入*」\(Bootstrapping\)。  
  
 當 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 安裝在您的開發電腦時，Power Packs 啟動載入器 \(Bootstrapper\) 套件就會加入至 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 啟動載入器目錄中。  接著，當您遵循程序加入 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 或 Windows Installer 部署的必要條件時，就可以使用這個套件。  
  
 啟動載入的元件預設會從與安裝套件相同的位置進行部署。  或者，您也可以視需要選擇從使用者可下載元件的 URL 或檔案共用位置來部署元件。  
  
> [!NOTE]
>  若要安裝已啟動載入的元件，使用者可能需要該電腦的系統管理或類似的使用者權限。  若為 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 應用程式，則不論應用程式所指定的安全性層級為何，使用者都需要系統管理權限才能安裝應用程式。  安裝應用程式之後，使用者不需系統管理權限即可執行應用程式。  
  
 安裝時，如果目的電腦中沒有 Power Packs 控制項，則會提示使用者安裝此控制項。  
  
 您也可以使用電子軟體散發系統 \(如 Microsoft Systems Management Server\) 預先部署 Power Packs 控制項，做為啟動載入的替代方式。  
  
## 請參閱  
 [How to: Install Prerequisites in Windows Installer Deployment](http://msdn.microsoft.com/zh-tw/653fc868-2486-429c-b75e-2f9d0c7f6619)   
 [如何：使用 ClickOnce 應用程式安裝必要條件](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [Not in Build: Choosing a Deployment Strategy](http://msdn.microsoft.com/zh-tw/ecd632d8-063c-4028-b785-81bba045107b)   
 [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)