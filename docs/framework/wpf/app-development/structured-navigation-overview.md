---
title: 結構化巡覽概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 8760c847d9e73fdff9f10f0dfa55a6c674021667
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364182"
---
# <a name="structured-navigation-overview"></a>結構化巡覽概觀

可由[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] 、或所<xref:System.Windows.Navigation.NavigationWindow>裝載的內容是由可由套件識別並由超連結流覽至的頁面所組成。 <xref:System.Windows.Controls.Frame> 頁面的結構及其可被巡覽的方式，如超連結所定義，稱之為巡覽拓撲。 這種拓撲適合各種不同的應用程式類型，尤其是巡覽文件的應用程式。 針對這類應用程式，使用者可以從一頁巡覽到另一頁，頁面彼此間不需要了解。

不過，其他類型的應用程式有需要知道被巡覽的頁面。 例如，假設人力資源應用程式有列出組織中所有員工的頁面：「員工清單」頁面。 此頁面也允許使用者按一下超連結新增新進員工。 按一下時，頁面會巡覽至「新增員工」頁面，收集新進員工的詳細資料，並傳回「員工清單」頁面建立新的員工以及更新清單。 這種巡覽樣式類似於呼叫方法執行一些處理並傳回值，稱之為結構化程式設計。 因此，這種巡覽稱之為「結構化巡覽」  。

<xref:System.Windows.Controls.Page>類別不會執行結構化導覽的支援。 相反地, <xref:System.Windows.Navigation.PageFunction%601>類別衍生自<xref:System.Windows.Controls.Page> , 並以結構化導覽所需的基本結構來擴充它。 本主題說明如何使用<xref:System.Windows.Navigation.PageFunction%601>來建立結構化導覽。

<a name="Structured_Navigation"></a>

## <a name="structured-navigation"></a>結構化巡覽

當一個頁面在結構化巡覽中呼叫另一個頁面時，需要下列部分或全部行為︰

- 呼叫端頁面會巡覽至呼叫的頁面，並選擇性地傳遞被呼叫頁面所需的參數。

- 當使用者用完呼叫端頁面時，呼叫的頁面會選擇性特別傳回給呼叫端頁面︰

  - 傳回狀態資訊，說明如何完成呼叫端頁面 (例如，使用者按下 [確定] 按鈕或 [取消] 按鈕)。

  - 傳回收集的使用者資料 (例如，新進員工的詳細資料)。

- 當呼叫端頁面傳回被呼叫的頁面時，巡覽記錄會移除呼叫的頁面，隔離呼叫頁面中的各個執行個體。

下圖說明這些行為:

![螢幕擷取畫面顯示呼叫頁面和呼叫頁面之間的流程。](./media/structured-navigation-overview/flow-between-calling-page-called-page.png)

您可以使用<xref:System.Windows.Navigation.PageFunction%601>做為所呼叫的頁面, 來執行這些行為。

<a name="Structured_Navigation_with_PageFunction"></a>

## <a name="structured-navigation-with-pagefunction"></a>有 PageFunction 的結構化巡覽

本主題說明如何執行涉及單一<xref:System.Windows.Navigation.PageFunction%601>的結構化導覽的基本機制。 在此範例中, <xref:System.Windows.Controls.Page>會<xref:System.Windows.Navigation.PageFunction%601>呼叫以從使用者<xref:System.String>取得值, 並將其傳回。

### <a name="creating-a-calling-page"></a>建立呼叫端頁面

呼叫<xref:System.Windows.Navigation.PageFunction%601>的頁面可以<xref:System.Windows.Controls.Page>是或<xref:System.Windows.Navigation.PageFunction%601>。 在此範例中, 它是<xref:System.Windows.Controls.Page>, 如下列程式碼所示。

[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]

[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]

### <a name="creating-a-page-function-to-call"></a>建立呼叫頁面函式

因為呼叫的頁面可以使用呼叫的頁面來收集並傳回使用者的資料, 所以<xref:System.Windows.Navigation.PageFunction%601>會實作為泛型類別, 其型別引數會指定所呼叫的頁面將傳回的數值型別。 下列程式碼會使用<xref:System.Windows.Navigation.PageFunction%601>傳回的, <xref:System.String>以顯示呼叫的頁面的初始執行。

[!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]

[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]

的宣告類似于的<xref:System.Windows.Controls.Page>宣告, 並加入型別引數。 <xref:System.Windows.Navigation.PageFunction%601> 如您在程式碼範例中所見，使用 `x:TypeArguments` 屬性的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記和使用標準泛型型別引數語法的程式碼後置，兩者都指定型別引數。

您不需要只使用 .NET Framework 類別做為型別引數。 <xref:System.Windows.Navigation.PageFunction%601>可以呼叫來收集抽象為自訂類型的定義域特定資料。 下列程式碼示範如何使用自訂類型做為的型別引數<xref:System.Windows.Navigation.PageFunction%601>。

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]

[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]

的型別引數<xref:System.Windows.Navigation.PageFunction%601>提供呼叫頁面與所呼叫頁面之間通訊的基礎, 下列各節將討論這些程式。

如您所見, 使用<xref:System.Windows.Navigation.PageFunction%601>宣告所識別的類型在將資料<xref:System.Windows.Navigation.PageFunction%601>從傳回至呼叫的頁面時, 扮演著重要的角色。

### <a name="calling-a-pagefunction-and-passing-parameters"></a>呼叫 PageFunction 並傳遞參數

若要呼叫頁面, 呼叫的頁面必須具現化所呼叫的頁面, 並使用<xref:System.Windows.Navigation.NavigationService.Navigate%2A>方法流覽至該網頁。 這可讓呼叫端頁面將初始資料傳遞至呼叫的頁面，例如由呼叫的頁面所收集之資料的預設值。

下列程式碼顯示已呼叫的頁面, 其中包含非參數的函式, 可接受來自呼叫端頁面的參數。

[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]

下列程式碼顯示處理<xref:System.Windows.Documents.Hyperlink.Click>的事件<xref:System.Windows.Documents.Hyperlink>的呼叫頁面, 以具現化呼叫的頁面, 並將初始字串值傳遞給它。

[!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]

您不需要將參數傳遞給呼叫的頁面。 您反而可以執行下列作業︰

- 從呼叫端頁面︰

  1. 使用無參數<xref:System.Windows.Navigation.PageFunction%601>的函式將呼叫的具現化。

  2. 將參數儲存在<xref:System.Windows.Application.Properties%2A>中。

  3. 流覽至呼叫<xref:System.Windows.Navigation.PageFunction%601>的。

- 從呼叫<xref:System.Windows.Navigation.PageFunction%601>的:

  - 取出並使用中<xref:System.Windows.Application.Properties%2A>儲存的參數。

但是，您很快就會發現，您還是需要使用程式碼來具現化並巡覽至呼叫的頁面，才能收集呼叫的頁面所傳回的資料。 <xref:System.Windows.Navigation.PageFunction%601>基於這個理由, 必須保持運作, 否則當您下次流覽<xref:System.Windows.Navigation.PageFunction%601>至時, 會<xref:System.Windows.Navigation.PageFunction%601>使用無參數的[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]函式來具現化。

但在呼叫的頁面傳回之前，它需要傳回呼叫端頁面可擷取的資料。

### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>將工作的工作結果和工作資料傳回給呼叫端頁面

使用者用完呼叫的頁面時，如本例所示，按 [確定] 或 [取消] 按鈕，必須傳回呼叫的頁面。 因為呼叫端頁面使用了被呼叫頁面來收集使用者資料，所以呼叫端頁面需要兩種類型的資訊︰

1. 使用者是否取消了呼叫的頁面 (本例中為按下 [確定] 按鈕或 [取消] 按鈕)。 這可讓呼叫端頁面決定是否要處理呼叫端頁面收集的使用者資料。

2. 使用者提供的資料。

若要傳回信息<xref:System.Windows.Navigation.PageFunction%601> , 請<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>執行方法。 下列程式碼示範如何呼叫它。

[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]

在本例中，如果使用者按下 [取消] 按鈕，`null` 值就會傳回呼叫端頁面。 如果改按下 [確定] 按鈕，則傳回使用者提供的字串值。 <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>是您呼叫的方法,可將您的資料傳回給呼叫的頁面。`protected virtual` 您的資料必須封裝在泛型<xref:System.Windows.Navigation.ReturnEventArgs%601>型別的實例中, 其型別引數會指定傳回<xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A>值的型別。 如此一來, 當您宣告具有<xref:System.Windows.Navigation.PageFunction%601>特定類型引數的時, 您會指出<xref:System.Windows.Navigation.PageFunction%601>將會傳回類型引數所指定之類型的實例。 在此範例中, 類型引數和, 因此傳回值的類型<xref:System.String>為。

呼叫<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>時, 呼叫端頁面需要某種方式來接收的傳回值<xref:System.Windows.Navigation.PageFunction%601>。 基於這個理由, <xref:System.Windows.Navigation.PageFunction%601>會執行<xref:System.Windows.Navigation.PageFunction%601.Return>呼叫要處理之頁面的事件。 當<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>呼叫時, <xref:System.Windows.Navigation.PageFunction%601.Return>會引發, 因此<xref:System.Windows.Navigation.PageFunction%601.Return>呼叫的頁面可以向註冊以接收通知。

[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]

### <a name="removing-task-pages-when-a-task-completes"></a>工作完成時移除工作頁面

當傳回呼叫的頁面，而使用者未取消呼叫的頁面時，呼叫端頁面會處理使用者提供以及呼叫的頁面所傳回的資料。 以此方式擷取的資料通常是獨立的活動。當被呼叫頁面傳回時，呼叫端頁面需要建立並巡覽至新的呼叫端頁面，以擷取更多資料。

不過，除非從日誌移除呼叫的頁面，否則使用者就能夠巡覽回到呼叫端頁面的上一個執行個體。 是否保留在日誌中是由<xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>屬性所決定。 <xref:System.Windows.Navigation.PageFunction%601> 根據預設, 當呼叫時<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> , 會自動移除頁面函式, 因為<xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>設定`true`為。 若要在呼叫之後<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> , 將頁面函式保留在導覽歷程記錄中, 請將設定<xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>為`false`。

<a name="Other_Types_of_Structured_Navigation"></a>

## <a name="other-types-of-structured-navigation"></a>其他類型的結構化巡覽

本主題說明的最基本用法<xref:System.Windows.Navigation.PageFunction%601> , 以支援呼叫/傳回結構化導覽。 此基礎讓您能夠建立更複雜的結構化巡覽類型。

例如，呼叫端頁面有時候需要多個頁面來收集足夠的使用者資料，或執行工作。 使用多個頁面稱之為「精靈」。

在其他情況下，應用程式可能會令相依於結構化巡覽的複雜巡覽拓撲有效運作。 如需詳細資訊，請參閱[巡覽拓撲概觀](navigation-topologies-overview.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [巡覽拓撲概觀](navigation-topologies-overview.md)
