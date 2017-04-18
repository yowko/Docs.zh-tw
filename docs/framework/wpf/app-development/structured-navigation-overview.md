---
title: "結構化巡覽概觀 | Microsoft Docs"
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
  - "結構化巡覽 [WPF]"
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
caps.latest.revision: 43
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 36
---
# 結構化巡覽概觀
[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]、<xref:System.Windows.Controls.Frame> 或 <xref:System.Windows.Navigation.NavigationWindow> 可裝載的內容是由頁面所組成，這些頁面可由套件的 [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] 識別，而且可使用超連結巡覽。  頁面的結構和巡覽頁面的方式 \(如超連結所定義\) 稱為巡覽拓撲。  這種拓撲適合各種應用程式類型，特別是巡覽文件的應用程式。  針對這類應用程式，使用者可以從一頁巡覽到另一頁，而各頁面無須知道彼此的內容。  
  
 不過，其他應用程式類型的頁面則需要知道有巡覽關係的頁面。  例如，假設人力資源應用程式有一頁列出組織中的所有員工，這頁稱為「列出員工」頁面。  此頁也可讓使用者按一下超連結來加入新員工。  按下超連結時，頁面會巡覽至「加入員工」頁面以收集新員工的詳細資料，然後將這些資料傳回「列出員工」頁面，以建立新員工並更新清單。  這種巡覽方式類似於呼叫方法來進行處理並傳回值的結構化程式設計。  因此，這種巡覽方式就稱為「*結構化巡覽*」\(Structured Navigation\)。  
  
 <xref:System.Windows.Controls.Page> 類別不會實作結構化巡覽的支援。  相反地，<xref:System.Windows.Navigation.PageFunction%601> 類別會衍生自 <xref:System.Windows.Controls.Page>，並擴充加入結構化巡覽所需的基本建構。  本主題顯示如何使用 <xref:System.Windows.Navigation.PageFunction%601> 建立結構化巡覽。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Structured_Navigation"></a>   
## 結構化巡覽  
 當某個頁面呼叫結構化巡覽中的另一頁面時，需要下列部分或所有行為：  
  
-   呼叫頁面會巡覽至被呼叫頁面，並選擇性傳遞被呼叫頁面所需的參數。  
  
-   當使用者使用完呼叫頁面後，被呼叫頁面會特別回到呼叫頁面，並選擇性：  
  
    -   傳回描述呼叫頁面如何完成的狀態資訊 \(例如，使用者是按 \[確定\] 按鈕或 \[取消\] 按鈕\)。  
  
    -   傳回使用者所提供的資料 \(例如新員工的詳細資料\)。  
  
-   當呼叫頁面回到被呼叫頁面時，被呼叫頁面會從巡覽記錄移除，以將被呼叫頁面的執行個體隔離開來。  
  
 下圖說明這些行為。  
  
 ![呼叫端頁面和被呼叫端頁面之間的流程](../../../../docs/framework/wpf/app-development/media/structurednavigationoverviewfigure1.png "StructuredNavigationOverviewFigure1")  
  
 您可以使用 <xref:System.Windows.Navigation.PageFunction%601> 當做被呼叫頁面，以實作這些行為。  
  
<a name="Structured_Navigation_with_PageFunction"></a>   
## 使用 PageFunction 進行結構化巡覽  
 本主題顯示如何實作使用單一 <xref:System.Windows.Navigation.PageFunction%601> 的結構化巡覽基本機制。  在這個範例中，<xref:System.Windows.Controls.Page> 會呼叫 <xref:System.Windows.Navigation.PageFunction%601> 以取得使用者提供的 <xref:System.String> 並傳回它。  
  
### 建立呼叫頁面  
 呼叫 <xref:System.Windows.Navigation.PageFunction%601> 的頁面可以是 <xref:System.Windows.Controls.Page> 或 <xref:System.Windows.Navigation.PageFunction%601>。  在這個範例中，這是 <xref:System.Windows.Controls.Page>，如下列程式碼所示。  
  
 [!code-xml[StructuredNavigationSample#CallingPageDefaultMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]  
[!code-xml[StructuredNavigationSample#CallingPageDefaultMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]  
  
 [!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
 [!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]  
  
### 建立頁面函式進行呼叫  
 由於呼叫頁面可使用被呼叫頁面收集和傳回使用者提供的資料，因此 <xref:System.Windows.Navigation.PageFunction%601> 會實作為泛型類別，其型別引數會指定被呼叫頁面傳回值的型別。  下列程式碼顯示被呼叫頁面的初始實作，其使用傳回 <xref:System.String> 的 <xref:System.Windows.Navigation.PageFunction%601>。  
  
 [!code-xml[StructuredNavigationSample#CalledPageFunctionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]  
  
 [!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
 [!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]  
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]  
  
 <xref:System.Windows.Navigation.PageFunction%601> 的宣告和 <xref:System.Windows.Controls.Page> 宣告類似，不過還加入了型別引數。  如程式碼範例所示，型別引數同時在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記 \(使用 `x:TypeArguments` 屬性\) 和程式碼後置 \(使用標準泛型型別引數語法\) 中指定。  
  
 不一定只有 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 類別才能當做型別引數。  您可以呼叫 <xref:System.Windows.Navigation.PageFunction%601> 收集提取為自訂型別的定義域特定資料。  下列程式碼顯示如何使用自訂型別做為 <xref:System.Windows.Navigation.PageFunction%601> 的型別引數。  
  
 [!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
 [!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]  
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]  
  
 [!code-xml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]  
[!code-xml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]  
  
 [!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
 [!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]  
  
  
 <xref:System.Windows.Navigation.PageFunction%601> 的型別引數提供呼叫頁面與被呼叫頁面之間的通訊基礎，這將在下列章節討論。  
  
 您將會了解，使用 <xref:System.Windows.Navigation.PageFunction%601> 宣告所識別的型別，在將資料從 <xref:System.Windows.Navigation.PageFunction%601> 傳回到呼叫頁面上，扮演了重要角色。  
  
### 呼叫 PageFunction 和傳遞參數  
 若要呼叫頁面，呼叫頁面必須將被呼叫頁面執行個體化，並使用 <xref:System.Windows.Navigation.NavigationService.Navigate%2A> 方法巡覽至該頁面。  這可讓呼叫頁面將初始資料傳遞至被呼叫頁面，例如要讓被呼叫頁面收集之資料的預設值。  
  
 下列程式碼顯示所呼叫的頁面，它使用非預設建構函式接受來自呼叫頁面的參數。  
  
 [!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
 [!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]  
  
 下列程式碼顯示呼叫頁面處理 <xref:System.Windows.Documents.Hyperlink.Click> \(將被呼叫頁面執行個體化並傳遞初始字串值給它\) 的 <xref:System.Windows.Documents.Hyperlink> 事件。  
  
 [!code-xml[StructuredNavigationSample#PassingDataMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]  
  
 您不需要傳遞參數給被呼叫頁面。  您可以改執行以下動作：  
  
-   從呼叫頁面：  
  
    1.  使用預設建構函式將被呼叫的 <xref:System.Windows.Navigation.PageFunction%601> 執行個體化。  
  
    2.  將參數儲存在 <xref:System.Windows.Application.Properties%2A>。  
  
    3.  巡覽至被呼叫的 <xref:System.Windows.Navigation.PageFunction%601>。  
  
-   從被呼叫的 <xref:System.Windows.Navigation.PageFunction%601>：  
  
    -   擷取並使用儲存在 <xref:System.Windows.Application.Properties%2A> 的參數。  
  
 但是，如稍後所見，您還是需要使用程式碼將被呼叫頁面執行個體化並巡覽至該頁面，才能收集被呼叫頁面傳回的資料。  因此，<xref:System.Windows.Navigation.PageFunction%601> 需要保持運作，否則下次巡覽至 <xref:System.Windows.Navigation.PageFunction%601> 時，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會使用預設建構函式將 <xref:System.Windows.Navigation.PageFunction%601> 執行個體化。  
  
 不過，在被呼叫頁面返回之前，它需要傳回可由呼叫頁面擷取的資料。  
  
### 傳回工作的工作結果和工作資料給呼叫頁面  
 一旦使用者使用完被呼叫頁面 \(此範例是按下 \[確定\] 或 \[取消\] 按鈕來表示\)，被呼叫頁面就需要返回。  由於呼叫頁面是使用被呼叫頁面收集使用者提供的資料，因此呼叫頁面需要兩種類型的資訊：  
  
1.  使用者是否取消了被呼叫頁面 \(此範例是藉由按下 \[確定\] 或 \[取消\] 按鈕\)。  這可讓呼叫頁面判斷是否要處理呼叫頁面從使用者收集到的資料。  
  
2.  使用者所提供的資料。  
  
 為傳回資訊，<xref:System.Windows.Navigation.PageFunction%601> 會實作 <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> 方法。  下列程式碼顯示如何呼叫它。  
  
 [!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
 [!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]  
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]  
  
 在這個範例中，如果使用者按下 \[取消\] 按鈕，就會傳回 `null` 值給呼叫頁面。  如果已按下 \[確定\] 按鈕，則會傳回使用者提供的字串值。  <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> 是 `protected` `virtual` 方法，呼叫該方法可將您的資料傳回呼叫頁面。  您的資料必須封裝在泛型 <xref:System.Windows.Navigation.ReturnEventArgs%601> 型別的執行個體中，此型別的型別引數會指定 <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> 傳回值的型別。  如此一來，當您使用特定型別引數宣告 <xref:System.Windows.Navigation.PageFunction%601> 時，就表示 <xref:System.Windows.Navigation.PageFunction%601> 會傳回型別引數所指定型別的執行個體。  在這個範例中，型別引數以及後來的傳回值都屬於型別 <xref:System.String>。  
  
 呼叫 <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> 時，呼叫頁面需要想辦法接收 <xref:System.Windows.Navigation.PageFunction%601> 的傳回值。  因此，<xref:System.Windows.Navigation.PageFunction%601> 會實作 <xref:System.Windows.Navigation.PageFunction%601.Return> 事件讓呼叫頁面處理。  當呼叫 <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> 時，會引發 <xref:System.Windows.Navigation.PageFunction%601.Return>，所以呼叫頁面可向 <xref:System.Windows.Navigation.PageFunction%601.Return> 註冊來接收通知。  
  
 [!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
 [!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]  
  
### 工作完成時移除工作頁面  
 當被呼叫頁面返回而使用者未取消被呼叫頁面時，呼叫頁面會處理使用者所提供的資料以及被呼叫頁面傳回的資料。  這種資料擷取方式通常是獨立進行的活動；當被呼叫頁面返回時，呼叫頁面需要建立並巡覽至新的呼叫頁面，以擷取更多的資料。  
  
 不過，除非從[日誌](GTMT)移除被呼叫頁面，否則使用者仍可巡覽回到呼叫頁面的前一個執行個體。  <xref:System.Windows.Navigation.PageFunction%601> 是否保留在[日誌](GTMT)，取決於 <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> 屬性。  依預設，呼叫 <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> 時會自動移除頁面函式，這是因為 <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> 設為 `true`。  若要在呼叫 <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> 之後將頁面函式保留在巡覽記錄中，請將 <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> 設為 `false`。  
  
<a name="Other_Types_of_Structured_Navigation"></a>   
## 其他結構化巡覽類型  
 本主題示範了最基本的 <xref:System.Windows.Navigation.PageFunction%601> 用法，以支援呼叫\/返回結構化巡覽。  您可以此為基礎，建立更複雜的結構化巡覽類型。  
  
 例如，呼叫頁面可能需要多個頁面才能向使用者收集足夠的資料或執行工作。  多個頁面的用法稱為「精靈」。  
  
 在其他情況下，應用程式可能有複雜的巡覽拓撲，需要依賴結構化巡覽才能有效運作。  如需詳細資訊，請參閱 [巡覽拓撲概觀](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Navigation.PageFunction%601>   
 <xref:System.Windows.Navigation.NavigationService>   
 [巡覽拓撲概觀](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)