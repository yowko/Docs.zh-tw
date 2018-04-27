---
title: 疑難排解互通性 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability [Visual Basic]
- interoperability, troubleshooting
- COM interop [Visual Basic], troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3ff175a0f8d152febf2d50c294d401b12285fc7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-interoperability-visual-basic"></a>疑難排解互通性 (Visual Basic)
當您 COM 和 managed 程式碼之間的交互操作[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]，您可能會遇到一或多個下列常見的問題。  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a> Interop 封送處理  
 有時候，您可能要使用資料型別不屬於[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。 Interop 組件處理大部分的 COM 物件的工作，但您可能要控制受管理的物件會公開至 COM 時所使用的資料型別 例如，類別庫中的結構必須指定`BStr`unmanaged 字串傳送至 Visual Basic 6.0 及舊版所建立的 COM 物件的類型。 在這種情況下，您可以使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>造成到即將公開為 unmanaged 類型的 managed 的類型的屬性。  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a> 匯出至 Unmanaged 程式碼的固定長度字串  
 在 Visual Basic 6.0 及舊版中，字串會匯出至 COM 物件為不含結束 null 字元的位元組序列。 與其他語言的相容性，Visual Basic.NET 包含終止字元匯出字串時。 若要解決此不相容，最好是將缺少的終止字元陣列的字串匯出`Byte`或`Char`。  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a> 匯出的繼承階層  
 Managed 的類別階層壓平合併時，公開為 COM 物件時。 例如，如果您是成員，來定義基底類別，則會繼承基底類別會公開為 COM 物件的衍生類別中使用衍生的類別中的 COM 物件的用戶端將無法使用繼承的成員。 可以從 COM 物件存取基底類別成員，只能當做基底類別的執行個體，然後才在基底類別也會建立為 COM 物件。  
  
## <a name="overloaded-methods"></a>多載的方法  
 雖然您可以使用 Visual Basic 中建立多載的方法，並不支援供 com 使用。 包含多載的方法的類別會公開為 COM 物件，都會產生新的方法名稱的多載的方法。  
  
 例如，假設有一個類別具有兩個多載`Synch`方法。 當類別為 COM 物件公開時，可能是新產生的方法名稱`Synch`和`Synch_2`。  
  
 重新命名可能會造成兩個問題的 COM 物件的取用者。  
  
1.  用戶端可能不會產生的方法名稱。  
  
2.  新的多載加入至類別或其基底類別時，可以變更公開為 COM 物件的類別中產生的方法名稱。 這可能會造成版本控制問題。  
  
 若要解決這兩個問題，請為每一種方法唯一的名稱，而不是使用多載中，當您開發即將公開為 COM 物件的物件。  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a> 使用 COM 物件，透過 Interop 組件  
 您在幾乎如同它們是 managed 程式碼取代所代表的 COM 物件使用 interop 組件。 不過，因為它們是包裝函式並不是實際的 COM 物件時，會使用 interop 組件和標準的組件之間的一些差異。 這些差異的部分包括公開的類別，以及資料型別參數和傳回值。  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a> 公開為這兩個介面的類別和類別  
 不同於標準的組件中的類別，COM 類別會公開介面和類別，表示在 COM 類別的 interop 組件中。 有相同的 COM 類別的介面名稱。 Interop 的類別名稱是原始的 COM 類別相同，但是字附加 「 類別 」。 例如，假設您有在專案中使用 interop 組件以取得 COM 物件的參考。 如果 COM 類別的名稱為`MyComClass`，IntelliSense 和物件瀏覽器會顯示名為介面`MyComClass`和類別，名為`MyComClassClass`。  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a> 建立.NET Framework 類別的執行個體  
 一般而言，您建立的執行個體[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]類別使用`New`陳述式的類別名稱。 Interop 組件所表示之 COM 類別是一種情況，您可以使用`New`陳述式的介面。 除非您正在使用的 COM 類別`Inherits`陳述式，就像類別一樣，您可以使用的介面。 下列程式碼示範如何建立`Command`擁有 Microsoft ActiveX 資料物件 2.8 程式庫 COM 物件參考的專案中的物件：  
  
 [!code-vb[VbVbalrInterop#20](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 不過，如果您使用之 COM 類別作為基底之衍生類別，您必須使用 interop 類別代表 COM 類別，如下列程式碼所示：  
  
 [!code-vb[VbVbalrInterop#21](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  Interop 組件隱含實作介面來代表 COM 類別。 您不應該嘗試使用`Implements`會造成陳述式來實作這些介面或錯誤。  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a> 資料型別參數和傳回值  
 不同於標準的組件的成員，interop 組件成員可能具有不同於原始物件宣告中所使用的資料類型。 雖然隱含 interop 組件會將 COM 類型轉換成相容的 common language runtime 類型中，您應該注意兩方用來避免在執行階段錯誤的資料類型。 例如，在 Visual Basic 6.0 及舊版中，類型的值中建立的 COM 物件`Integer`假設[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]對等型别， `Short`。 建議您使用物件瀏覽器，來檢查已匯入成員的特性，才使用。  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a> 模組層級 COM 方法  
 大部分的 COM 物件可用來建立 COM 類別使用的執行個體`New`關鍵字，然後再呼叫物件的方法。 這項規則有一個例外狀況包含 COM 物件，包含`AppObj`或`GlobalMultiUse`COM 類別。 這種類別類似於 Visual Basic.NET 類別中的模組層級方法。 Visual Basic 6.0 及舊版隱含地建立這類物件的執行個體為您第一次，讓您呼叫其方法的其中一個。 例如，Visual Basic 6.0 中您可以加入 Microsoft DAO 3.6 物件程式庫並呼叫參考`DBEngine`方法，而不先建立執行個體：  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic.NET，您必須一律建立 COM 物件的執行個體才能使用它們的方法。 若要在 Visual Basic 中使用這些方法，將變數宣告為所需的類別，並使用新的關鍵字來將物件指派給物件變數。 `Shared`可以使用關鍵字，當您想要確定建立類別，只有一個執行個體。  
  
 [!code-vb[VbVbalrInterop#23](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a> 事件處理常式中的未處理的錯誤  
 一個常見的 interop 問題包含處理 COM 物件所引發的事件的事件處理常式中的錯誤。 這類錯誤會被忽略，除非您特別要檢查是否有錯誤使用`On Error`或`Try...Catch...Finally`陳述式。 例如，下列範例是從 Visual Basic.NET 專案具有 Microsoft ActiveX 資料物件 2.8 程式庫 COM 物件的參考。  
  
 [!code-vb[VbVbalrInterop#24](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 此範例中會如預期般引發錯誤。 不過，如果您嘗試不相同的範例`Try...Catch...Finally`區塊中，錯誤會被忽略，方式就如同您使用`OnError Resume Next`陳述式。 沒有錯誤處理，將 「 除以零以無訊息模式失敗。 因為這類錯誤永遠不會引發未處理例外狀況的錯誤，很重要，您會使用某種形式的事件處理常式處理事件從 COM 物件的例外狀況處理。  
  
### <a name="understanding-com-interop-errors"></a>了解 COM interop 錯誤  
 不需要錯誤處理 interop 呼叫通常會產生錯誤，提供一些資訊。 您應該盡可能使用結構化處理，以提供問題的相關資訊，所發生的錯誤。 當您偵錯應用程式時，這可以是特別有用。 例如:   
  
 [!code-vb[VbVbalrInterop#25](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 您可以檢查例外狀況物件的內容來找到錯誤描述、 HRESULT，以及 COM 錯誤的來源等資訊。  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a> ActiveX 控制項問題  
 大部分的 ActiveX 控制項可搭配 Visual Basic 6.0 使用 Visual Basic.NET 運作時發生問題。 主要的例外狀況是容器控制項中或以視覺化方式包含其他控制項的控制項。 無法以正常運作的舊版控制項的一些範例[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]如下：  
  
-   Microsoft Forms 2.0 框架控制項  
  
-   上下按鈕控制項，也就是微調控制項  
  
-   Sheridan 索引標籤控制項  
  
 有只有少數的因應措施不支援的 ActiveX 控制項問題。 您可以移轉現有的控制項，[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]如果您擁有原始的原始程式碼。 否則，您可以洽詢軟體廠商更新。ActiveX 控制項不支援的網路相容版本的控制項來取代。  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a> 傳遞的控制項 ByRef 的 ReadOnly 屬性  
 Visual Basic.NET 有時會引發 COM 錯誤，例如，「 錯誤 0x800A017F CTL_E_SETNOTSUPPORTED"，當您將傳遞`ReadOnly`的一些較舊的 ActiveX 控制項做為屬性`ByRef`其他程序的參數。 從 Visual Basic 6.0 的類似程序呼叫不會引發錯誤，而且參數會視為以值傳遞。 Visual Basic.NET 錯誤訊息指出您要變更此屬性沒有屬性，`Set`程序。  
  
 如果您有存取呼叫程序，您可以使用來避免這個錯誤`ByVal`關鍵字來宣告參數接受`ReadOnly`屬性。 例如:   
  
 [!code-vb[VbVbalrInterop#26](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 如果您沒有存取原始碼所呼叫的程序，您可以強制以傳值加上一組額外的括號括住的呼叫程序的屬性。 例如，在具有 Microsoft ActiveX 資料物件 2.8 程式庫 COM 物件的參考專案中，您可以使用：  
  
 [!code-vb[VbVbalrInterop#27](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a> 部署 Interop 公開 （expose） 的組件  
 部署的 COM 介面公開 （expose） 的組件提供唯一的一些挑戰。 例如，個別應用程式參考相同的 COM 組件時，就會發生潛在的問題。 安裝新版的組件和另一個應用程式仍在使用舊版本的組件時，常會使用這種情況。 如果您解除安裝共用的 DLL 的組件，您會無意間造成它無法使用其他組件。  
  
 若要避免這個問題，您應該將共用的組件安裝到全域組件快取 (GAC) 中，並使用元件的合併模組。 如果您無法在 GAC 中安裝應用程式，它應該會安裝至 CommonFilesFolder 版本特定子目錄中。  
  
 不共用的組件應該位於與呼叫的應用程式目錄中的並排顯示。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (類型程式庫匯入工具)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (類型程式庫匯出工具)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [逐步解說：實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [全域組件快取](../../../framework/app-domains/gac.md)
