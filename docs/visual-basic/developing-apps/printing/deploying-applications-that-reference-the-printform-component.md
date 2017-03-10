---
title: "Deploying Applications That Reference the PrintForm Component (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "PrintForm component [Visual Basic], deploying"
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Deploying Applications That Reference the PrintForm Component (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

如果您想要部署參考 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件的應用程式，則該元件必須安裝在目的電腦上。  
  
 Visual Studio 中已不再包含 PowerPack 控制項，但您可以從[下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。  
  
## 安裝 PrintForm 作為必要條件  
 若要順利部署應用程式，您也必須部署應用程式參考的所有元件。 安裝必要條件元件的程序稱為*「啟動載入」*\(Bootstrapping\)。  
  
 將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件安裝到開發電腦時，會將 Microsoft Visual Basic Power Pack 啟動載入器套件加入 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 啟動載入器目錄中。 接著，當您遵循程序加入 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 或 Windows Installer 部署的必要條件時，就可以使用這個套件。  
  
 預設會從安裝套件所在的相同位置來部署啟動載入的元件。 或者，您也可以視需要選擇從使用者可下載元件的 URL 或檔案共用位置來部署元件。  
  
> [!NOTE]
>  若要安裝啟動載入的元件，使用者可能需要該電腦的系統管理或類似的使用者權限。 若為 [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick-md.md)] 應用程式，則不論應用程式所指定的安全性層級為何，使用者都需要系統管理權限才能安裝應用程式。 安裝應用程式之後，使用者不需要系統管理權限，即可執行應用程式。  
  
 在安裝期間，如果目的電腦上沒有 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件，則會提示使用者安裝此元件。  
  
 您可以使用電子軟體散發系統 \(例如 Microsoft Systems Management Server\) 來預先部署 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件，以取代啟動載入。  
  
## 請參閱  
 [如何：使用 ClickOnce 應用程式安裝必要條件](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [不在組建中：選擇部署策略](http://msdn.microsoft.com/zh-tw/ecd632d8-063c-4028-b785-81bba045107b)   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)