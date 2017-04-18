---
title: "疑難排解互通性 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability
- interoperability, troubleshooting
- COM interop, troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cbc37638ed5c57b94356c2d189f36b66202ceba5
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-interoperability-visual-basic"></a>疑難排解互通性 (Visual Basic)
當您 COM 和 managed 程式碼之間的相互操作[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]，您可能會遇到一或多個下列常見的問題。  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a>Interop 封送處理  
 有時候，您可能要使用資料型別不屬於[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]。 Interop 組件會處理大部分的 COM 物件的工作，但您也可以控制受管理的物件會公開給 COM 時所使用的資料型別 例如，類別庫中的結構必須指定`BStr`unmanaged 字串傳送至 Visual Basic 6.0 及較早版本所建立的 COM 物件的型別。 在這種情況下，您可以使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>造成 managed 型別公開為 unmanaged 類型的屬性。</xref:System.Runtime.InteropServices.MarshalAsAttribute>  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a>匯出至 Unmanaged 程式碼的固定長度字串  
 在 Visual Basic 6.0 和舊版中，字串會匯出至 COM 物件為不含 null 結尾字元的位元組序列。 與其他語言所撰寫的相容性[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]匯出字串時，包括終止字元。 若要解決這個不相容性的最佳方式是將缺少的終止字元陣列的字串匯出`Byte`或`Char`。  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a>匯出的繼承階層架構  
 Managed 的類別階層壓平合併時，公開為 COM 物件時。 例如，如果您的成員，定義基底類別，則繼承的基底類別公開為 COM 物件的衍生類別中，使用衍生的類別中的 COM 物件的用戶端將無法使用繼承的成員。 可以從 COM 物件存取基底類別成員，只能當做基底類別的執行個體，然後才在基底類別也會建立為 COM 物件。  
  
## <a name="overloaded-methods"></a>多載的方法  
 雖然您可以建立多載的方法與[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，COM 不支援 包含多載的方法的類別公開為 COM 物件時，都會產生新的方法名稱多載的方法。  
  
 例如，假設有兩個多載類別`Synch`方法。 當類別公開為 COM 物件時，可能是新產生的方法名稱`Synch`和`Synch_2`。  
  
 重新命名作業可能會造成兩個問題的 COM 物件的取用者。  
  
1.  用戶端可能不會產生的方法名稱。  
  
2.  新的多載加入至類別或其基底類別時，可以變更類別公開為 COM 物件中產生的方法名稱。 這可能會造成版本控制問題。  
  
 若要解決這兩個問題，請為每一種方法唯一的名稱，而不是使用多載，當您開發即將公開為 COM 物件的物件。  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a>使用 COM 物件透過 Interop 組件  
 幾乎就如同它們所表示的 COM 物件的 managed 程式碼取代項目，您可以使用 interop 組件。 不過，因為它們是包裝函式並不是實際的 COM 物件，是使用 interop 組件和標準組件之間的一些差異。 這些差異的部分包括公開的類別，以及參數和傳回值的資料型別。  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a>公開為這兩個介面的類別和類別  
 不同於標準的組件中的類別，COM 類別會公開介面和類別，表示 COM 類別的 interop 組件中。 相同的 COM 類別介面的名稱。 Interop 類別的名稱與原始的 COM 類別，相同但字附加 「 類別 」。 例如，假設您有專案的 COM 物件的 interop 組件的參考。 如果 COM 類別的名稱為`MyComClass`，IntelliSense 和物件瀏覽器會顯示名為介面`MyComClass`和類別，名為`MyComClassClass`。  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a>建立.NET Framework 類別的執行個體  
 一般來說，您建立的執行個體[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]類別使用`New`陳述式的類別名稱。 Interop 組件所表示的 COM 類別是一種情況，您可以使用`New`陳述式的介面。 除非您使用 COM 類別`Inherits`陳述式中，您可以使用介面，就像您一樣的類別。 下列程式碼示範如何建立`Command`Microsoft ActiveX 資料物件 2.8 程式庫 COM 物件的參考的專案中的物件︰  
  
 [!code-vb[VbVbalrInterop #&20;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 不過，如果您使用 COM 類別作為基底為衍生類別，您必須使用 interop 類別代表 COM 類別，如下列程式碼所示︰  
  
 [!code-vb[VbVbalrInterop #&21;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  Interop 組件以隱含方式實作代表 COM 類別的介面。 您不應該嘗試使用`Implements`會實作這些介面或錯誤的陳述式。  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a>資料型別參數和傳回值  
 不同於標準的組件的成員，interop 組件成員可能會與原始物件宣告中所使用的不同的資料型別。 雖然隱含 interop 組件會將 COM 型別轉換成相容的 common language runtime 類型中，您應該注意兩方用來避免在執行階段錯誤的資料型別。 例如，在 Visual Basic 6.0 及舊版中，類型的值中建立的 COM 物件`Integer`假設[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]對等型別， `Short`。 建議使用物件瀏覽器檢查匯入成員的特性，才能使用它們。  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a>模組層級 COM 方法  
 大部分的 COM 物件由建立使用 COM 類別的執行個體`New`關鍵字，然後再呼叫物件的方法。 此規則的唯一例外牽涉到 COM 物件，包含`AppObj`或`GlobalMultiUse`COM 類別。 這種類別類似於在模組層級方法[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]類別。 Visual Basic 6.0 及舊版隱含建立這類物件的執行個體，您呼叫其中一個方法的第一次。 例如，在 Visual Basic 6.0 中您可以加入 Microsoft DAO 3.6 物件程式庫和呼叫的參考`DBEngine`方法，而不先建立執行個體︰  
  
```  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]需要您永遠建立 COM 物件的執行個體，才能使用它們的方法。 若要使用這些方法在[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]，宣告所需類別的變數，並使用新的關鍵字來將物件指派給物件變數。 `Shared`可以使用關鍵字，當您想要確定建立的類別，只有一個執行個體。  
  
 [!code-vb[VbVbalrInterop #&23;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a>事件處理常式中未處理的錯誤  
 一個常見的 interop 問題牽涉到處理 COM 物件所引發的事件的事件處理常式中的錯誤。 這類錯誤會被忽略，除非您特別要檢查是否有錯誤使用`On Error`或`Try...Catch...Finally`陳述式。 例如，下列範例是從[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]Microsoft ActiveX 資料物件 2.8 程式庫 COM 物件參考的專案。  
  
 [!code-vb[VbVbalrInterop #&24;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 如預期般，這個範例會引發錯誤。 不過，如果您嘗試不含相同的範例`Try...Catch...Finally`區塊中，錯誤會被忽略，方式就如同您使用`OnError Resume Next`陳述式。 沒有錯誤處理除以零的無訊息地失敗。 因為這類錯誤永遠不會引發未處理例外狀況的錯誤，請務必您使用某種形式的例外狀況處理在處理從 COM 物件事件的事件處理常式。  
  
### <a name="understanding-com-interop-errors"></a>了解 COM interop 錯誤  
 不需要錯誤處理 interop 呼叫通常會產生錯誤提供少量的資訊。 請盡可能使用結構化處理，以提供有關問題的詳細資訊，所發生的錯誤。 當您偵錯應用程式時，這可以是特別有用。 例如:   
  
 [!code-vb[VbVbalrInterop #&25;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 您可以藉由檢查例外狀況物件的內容中找到錯誤描述、 HRESULT 和 COM 錯誤的來源等資訊。  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a>ActiveX 控制項的問題  
 大部分的 ActiveX 控制項可搭配 Visual Basic 6.0 搭配[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]沒有問題。 主要的例外狀況是容器控制項中或以視覺化方式包含其他控制項的控制項。 未使用正確的舊版控制項的一些範例[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]如下︰  
  
-   Microsoft Form 2.0 Frame 控制項  
  
-   上下按鈕控制項，也就是微調控制項  
  
-   Sheridan 索引標籤控制項  
  
 有不支援 ActiveX 控制項問題只有少數因應措施。 您可以移轉現有的控制項，[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]如果您有原始來源程式碼。 否則，您可以洽詢軟體廠商更新。NET 相容版本的控制項來取代不支援 ActiveX 控制項。  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a>傳遞的控制項 ByRef 的 ReadOnly 屬性  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]您傳遞時，有時候會發出 COM 錯誤，例如 「 錯誤 0x800A017F CTL_E_SETNOTSUPPORTED 」`ReadOnly`的某些較舊的 ActiveX 控制項做為屬性`ByRef`其他程序的參數。 從 Visual Basic 6.0 的類似程序呼叫不會引發錯誤，以及參數會視為以值傳遞。 在您看到的錯誤訊息[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]是報告您嘗試變更此屬性，並沒有屬性的 COM 物件`Set`程序。  
  
 如果您有存取所呼叫的程序，您可以藉由避免這個錯誤`ByVal`關鍵字來宣告參數接受`ReadOnly`屬性。 例如:   
  
 [!code-vb[VbVbalrInterop #&26;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 如果您沒有存取所呼叫的程序的原始程式碼，您可以強制以傳值加一組額外的括號括住呼叫程序的屬性。 例如，在專案中有 Microsoft ActiveX 資料物件 2.8 程式庫 COM 物件的參考，您可以使用︰  
  
 [!code-vb[VbVbalrInterop #&27;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a>部署 Interop 公開 （expose） 的組件  
 部署公開 COM 介面的組件提供一些特殊的問題。 比方說，當個別的應用程式參考相同的 COM 組件，就會發生潛在的問題。 這種情況時，一般在安裝新版本的組件和另一個應用程式仍在使用舊版本的組件。 如果您解除安裝共用 dll 檔的組件，您可以會不小心讓它無法使用其他組件。  
  
 若要避免這個問題，您應該安裝共用組件至全域組件快取 (GAC) 中，並使用合併模組元件。 如果您無法在 GAC 中安裝應用程式，它應該會安裝至 CommonFilesFolder 版本特定子目錄中。  
  
 不共用的組件應該位於與呼叫的應用程式目錄中的並排顯示。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute></xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Tlbimp.exe （類型程式庫匯入工具）](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)   
 [Tlbexp.exe （類型程式庫匯出工具）](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)   
 [逐步解說︰ 實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [全域組件快取](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)
