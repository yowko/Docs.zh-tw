---
title: "部署參考 PrintForm 元件 (Visual Basic) 的應用程式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 016643329d2ee66ca5a32f155cf91e0ee137f38f
ms.lasthandoff: 03/13/2017

---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>部署參考 PrintForm 元件 (Visual Basic) 的應用程式
如果您想要部署應用程式參考<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件，必須在目的地電腦上安裝的元件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
 Visual Studio 中已不再包含 PowerPack 控制項，但您可以從 [下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>安裝必須配合做為必要條件  
 若要順利部署應用程式，您也必須部署應用程式參考的所有元件。 安裝必要條件元件的程序稱為 *「啟動載入」*(Bootstrapping)。  
  
 當<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>開發電腦上已安裝元件，Microsoft Visual Basic Power Pack 啟動載入器套件會新增至[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]啟動載入器目錄。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 當您遵循的程序加入任何一項必要條件，就可以使用此套件[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]或 Windows Installer 部署。  
  
 預設會從安裝套件所在的相同位置來部署啟動載入的元件。 或者，您也可以視需要選擇從使用者可下載元件的 URL 或檔案共用位置來部署元件。  
  
> [!NOTE]
>  若要安裝啟動載入的元件，使用者可能需要該電腦的系統管理或類似的使用者權限。 如[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]應用程式，也就是說，使用者將會需要系統管理權限才能安裝應用程式，不論應用程式所指定的安全性層級。 安裝應用程式之後，使用者不需要系統管理權限，即可執行應用程式。  
  
 在安裝期間，將會提示使用者安裝<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>如果不存在於目的地電腦上的元件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
 若要啟動另外，您可以預先部署<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件使用電子軟體發佈系統，例如 Microsoft Systems Management Server。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
## <a name="see-also"></a>請參閱  
 [如何︰ 使用 ClickOnce 應用程式安裝必要條件](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5)   
 [PrintForm 元件](../../../visual-basic/developing-apps/printing/printform-component.md)
