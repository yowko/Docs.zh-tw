---
title: "如何：將 ActiveX 控制項加入至 Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 940dd21fc48c23ce623280aab2c487db5810057c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>如何：將 ActiveX 控制項加入至 Windows Form
Windows Form 設計工具最適合主機的 Windows Form 控制項，而您也可以使 Windows Form 上的 ActiveX 控制項。  
  
> [!CAUTION]
>  ActiveX 控制項新增到它們時，有適用於 Windows Form 的效能限制。  
  
 您將 ActiveX 控制項加入至表單之前，您必須將他們加入 [工具箱]。 如需詳細資訊，請參閱[COM 元件、 自訂工具箱對話方塊](http://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請在 [工具]  功能表上按一下 [匯入和匯出設定]  。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>若要將 ActiveX 控制項加入至您的 Windows Form  
  
-   按兩下 [工具箱] 控制項。  
  
     [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]將控制項的所有參考都加入專案中。 如需使用 Windows Form 上的 ActiveX 控制項時，請記住的事項的詳細資訊，請參閱[裝載 Windows Form 上的 ActiveX 控制項時的考量](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md)。  
  
    > [!NOTE]
    >  Windows Form ActiveX 控制項匯入工具 (AxImp.exe) 超過預期的 ActiveX 動態連結程式庫匯入作業時，會建立不同類型的事件引數。 AxImp.exe 所建立的引數都與下列類似： `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`，當`Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)`預期。 請注意，此不規則不會阻止程式碼正常運作。 如需詳細資訊，請參閱[Windows Form ActiveX 控制項匯入工具 (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)。  
  
## <a name="see-also"></a>請參閱  
 [Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)  
 [比較各種語言和程式庫的控制項與可以透過程式設計的物件](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [操作說明：將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [標記個別 Windows Forms 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [依功能區分 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
