---
title: "如何：將 ActiveX 控制項加入至 Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ActiveX 控制項 [Windows Form], 加入"
  - "表單, 加入 ActiveX 控制項"
  - "Windows Form 控制項, ActiveX 控制項"
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：將 ActiveX 控制項加入至 Windows Form
在將 Windows Form 設計工具最佳化以裝載 Windows Form 控制項時，您也可以把 ActiveX 控制項置入 Windows Form 內。  
  
> [!CAUTION]
>  將 ActiveX 控制項加入 Windows Form 之後，表單的效能會有所限制。  
  
 將 ActiveX 控制項加入表單之前，必須先將它們加入至 \[工具箱\]。  如需詳細資訊，請參閱[自訂工具箱對話方塊、COM 元件](http://msdn.microsoft.com/zh-tw/171333f3-f207-4e02-bbdc-17862556212c)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  如果要變更設定，請按一下 \[**工具**\] 功能表上的 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要將 ActiveX 控制項加入您的 Windows Form  
  
-   按兩下 \[工具箱\] 上的控制項。  
  
     [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 會將對這個控制項的所有參考全部加入到專案中。  如需在 Windows Form 上使用 ActiveX 控制項時所需注意的詳細資訊，請參閱[在 Windows Form 上裝載 ActiveX 控制項的考慮因素](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md)。  
  
    > [!NOTE]
    >  Windows Form ActiveX 控制項匯入工具 \(AxImp.exe\) 在匯入 ActiveX 動態連結程式庫時，會建立與預期不同類型的事件引數。  當 `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` 為預期的引數時，所建立的引數與下列引數相似：`Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`。  請注意此種不規則變化不會影響程式碼的正常運作。  如需詳細資訊，請參閱 [Windows Form ActiveX 控制項匯入工具 \(Aximp.exe\)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)。  
  
## 請參閱  
 [Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)   
 [Controls and Programmable Objects Compared in Various Languages and Libraries](http://msdn.microsoft.com/zh-tw/021f2a1b-8247-4348-a5ad-e1d9ab23004b)   
 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)   
 [排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [標記個別 Windows Form 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [依功能區分 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)