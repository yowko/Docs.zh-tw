---
title: "範例 OpenType 字型套件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "字型, OpenType 字型套件"
  - "OpenType 字型套件"
  - "印刷樣式, OpenType 字型套件"
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# 範例 OpenType 字型套件
本主題提供隨 [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] 散發之範例 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型的概觀。  這些範例字型支援 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式可以使用的 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 擴充功能。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="overview"></a>   
## OpenType 字型套件中的字型  
 [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] 提供一系列的範例 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型，您可以用於建立 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式。  這些範例字型都是依照 Ascender Corporation 的授權提供。  這些字型只會實作 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 格式定義之所有功能的子集。  下表列出範例 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型的名稱。  
  
|**名稱**|**檔案**|  
|------------|------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles Light|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 下圖顯示範例 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型的外觀。  
  
 ![列出範例字型套件中的字型名稱](../../../../docs/framework/wpf/advanced/media/samplefontpack01.png "samplefontpack01")  
OpenType 字型套件中的字型  
  
 這些範例字型都是依照 Ascender Corporation 的授權提供。  Ascender 是先進字型產品的供應商。  若要取得範例字型之擴充或自訂版本的授權，請參閱 [Ascender Corporation 的網站](http://go.microsoft.com/fwlink/?LinkId=182627) \(英文\)。  
  
> [!NOTE]
>  身為開發人員，您的職責是確保對於您內嵌在應用程式中或是以其他方式轉散發的任何字型，您必須擁有必要的授權權利。  
  
<a name="installing_the_fonts"></a>   
## 安裝字型  
 您可以選擇將範例 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型安裝到預設的 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Fonts 目錄 \(**\\WINDOWS\\Fonts**\) 中。  請使用 \[字型\] 控制台安裝字型。  將這些字型安裝到電腦上之後，所有參考預設 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 字型的應用程式就可以存取這些字型。您可以按兩下字型檔案，顯示包含幾種字型大小的代表性字元集合。  下列螢幕擷取畫面顯示 Lindsey 字型檔案 Linds.ttf。  
  
 ![Lindsey 字型 &#40;OpenType&#41;](../../../../docs/framework/wpf/advanced/media/typographyinwpf-04.png "TypographyInWPF\_04")  
顯示 Lindsey 字型  
  
<a name="using_the_fonts"></a>   
## 使用字型  
 在應用程式中使用字型的方式有兩種。  您可以在應用程式中加入字型做為專案內容項目，這些項目不會做為資源內嵌於組件內。  此外，您也可以在應用程式中加入字型做為專案資源項目，內嵌在應用程式的組件檔中。  如需詳細資訊，請參閱[將字型與應用程式一起封裝](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)。  
  
## 請參閱  
 <xref:System.Windows.Documents.Typography>   
 [OpenType 字型功能](../../../../docs/framework/wpf/advanced/opentype-font-features.md)   
 [將字型與應用程式一起封裝](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)