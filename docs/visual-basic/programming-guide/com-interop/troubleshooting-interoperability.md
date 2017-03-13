---
title: "Troubleshooting Interoperability (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interop, deploying assemblies"
  - "assemblies [Visual Basic]"
  - "interop, installing assemblies that share components"
  - "COM objects, troubleshooting"
  - "interop, sharing components"
  - "troubleshooting interoperability"
  - "interoperability, troubleshooting"
  - "COM interop, troubleshooting"
  - "assemblies [Visual Basic], deploying"
  - "troubleshooting Visual Basic, interoperability"
  - "interop assemblies"
  - "interoperability, sharing components"
  - "shared components, using with assemblies"
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Troubleshooting Interoperability (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

在 COM 和 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 的 Managed 程式碼之間進行互通時，您可能會遇到下列一項或多項常見的問題。  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a> Interop 封送處理  
 有時您必須使用不屬於 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 一部分的資料型別。  Interop 組件會處理 COM 物件的大部分作業，不過當將 Managed 物件公開給 COM 時，您可能必須控制所使用的資料型別。  例如，類別庫中的結構必須在傳送至 Visual Basic 6.0 \(含\) 更早版本所建立之 COM 物件的字串上，指定 `BStr` Unmanaged 型別。  在這種情況下，您可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，讓 Managed 型別公開為 Unmanaged 型別。  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a> 將固定長度字串匯出至 Unmanaged 程式碼  
 在 Visual Basic 6.0 \(含\) 更早版本中，字串是以一連串不含 null 終端字元的位元組匯出至 COM 物件。  為了與其他語言相容，[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] 在匯出字串時會包含終端字元。  若要解決這種不相容的問題，最好是將缺少終端字元的字串以 `Byte` 或 `Char` 的陣列形式匯出。  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a> 匯出繼承階層架構  
 當公開為 COM 物件時，Managed 類別階層架構會扁平化。  例如，如果您定義有個成員的基底類別，然後在公開為 COM 物件的衍生類別中繼承該基底類別時，則使用 COM 物件中該衍生類別的用戶端將無法使用繼承的成員。  基底類別成員只能在成為基底類別執行個體的情況下才能從 COM 物件存取，而且也必須將基底類別建立為 COM 物件才行。  
  
## 多載方法  
 雖然您可以用 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 建立多載方法，但 COM 不支援此功能。  以 COM 物件方式公開包含多載方法的類別時，將會為多載方法建立新的方法名稱。  
  
 例如，有一個類別包含 `Synch` 方法的兩個多載。  將該類別公開為 COM 物件時，新產生的方法名稱可能是 `Synch` 和 `Synch_2`。  
  
 重新命名可能對 COM 物件的消費者造成兩個問題。  
  
1.  用戶端可能未預期所產生的方法名稱。  
  
2.  公開為 COM 物件之類別中產生的方法名稱，可能會在新的多載加入至類別或其基底類別時變更，  如此可能會造成版本控制問題。  
  
 若要解決這兩個問題，在開發即將公開為 COM 物件的物件時，請為每個方法指定唯一的名稱，不要使用多載。  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a> 透過 Interop 組件使用 COM 物件  
 使用 Interop 組件的方式幾乎就像是將其當做所代表 COM 物件的 Managed 程式碼替代項目一樣。  不過，由於這些組件是包裝函式，而且也不是實質的 COM 物件，因此在使用 Interop 組件與使用標準組件之間還是有些差異。  這些差異的部分包括類別的公開以及參數和傳回值的資料型別。  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a> 類別同時公開為介面和類別  
 與標準組件中的類別不同的是，Interop 組件中的 COM 類別會同時公開為介面和代表 COM 類別的類別。  介面的名稱與 COM 類別的名稱完全相同。  Interop 類別的名稱則與原始 COM 類別相同，只不過另外附加 "Class" 一字。  例如，假設您有個專案參考一 COM 物件的 Interop 組件。  如果 COM 類別的名稱為 `MyComClass`，IntelliSense 和物件瀏覽器就會顯示名為 `MyComClass` 的介面和名為 `MyComClassClass` 的類別。  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a> 建立 .NET Framework 類別的執行個體  
 一般來說，您可以使用 `New` 陳述式搭配類別名稱，來建立 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 類別的執行個體。  要以 Interop 組件表示 COM 類別則可使用 `New` 陳述式搭配介面來這麼做。  除非您使用了包含 `Inherits` 陳述式的 COM 類別，否則就可像使用類別一樣來使用介面。  下列程式碼會示範如何在具有 Microsoft ActiveX Data Objects 2.8 Library COM 物件之參考的專案中，建立 `Command` 物件：  
  
 [!code-vb[VbVbalrInterop#20](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 不過，如果您將 COM 類別當做衍生類別的基礎使用的話，您就必須使用代表 COM 類別的 Interop 類別，如下列程式碼所示：  
  
 [!code-vb[VbVbalrInterop#21](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  Interop 組件會隱含實作代表 COM 類別的介面。  您不應該嘗試使用 `Implements` 陳述式實作這些介面，否則將會產生錯誤。  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a> 參數和傳回值的資料型別  
 Interop 組件成員與標準組件的成員不同，前者可能有些資料型別與原始物件宣告中所使用的資料型別不同。  雖然 Interop 組件會將 COM 型別隱含轉換為相容的 Common Language Runtime 型別，但您還是應注意兩邊所使用的資料型別，以避免執行階段錯誤。  例如，在以 Visual Basic 6.0 \(含\) 較早版本建立的 COM 物件中，`Integer` 型別的值會成為 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 的對等型別 `Short`。  建議您在使用匯入成員之前先使用物件瀏覽器來檢查其特性。  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a> 模組層級 COM 方法  
 大部分的 COM 物件是使用 `New` 關鍵字建立一個 COM 類別的執行個體，然後再藉此呼叫物件的方法。  這個規則的其中一個例外狀況會牽涉到包含 `AppObj` 或 `GlobalMultiUse` COM 類別的 COM 物件。  這樣的類別類似於 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] 類別中的模組層級方法。  在您第一次呼叫其中一個物件方法時，Visual Basic 6.0 \(含\) 較早版本會隱含建立這個物件的執行個體。  例如，在 Visual Basic 6.0 中您可以加入 Microsoft DAO 3.6 Object Library 的參考，並呼叫 `DBEngine` 方法，而不用先建立執行個體：  
  
```  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] 會要求您在使用其方法之前，一定要先建立 COM 物件的執行個體。  若要使用 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] 中的這些方法，請宣告所需類別的變數，並使用 new 關鍵字，將物件指定給物件變數。  當您要確定是否只建立了一個類別執行個體時，可以使用 `Shared` 關鍵字。  
  
 [!code-vb[VbVbalrInterop#23](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a> 事件處理常式中未處理的錯誤  
 處理常式內部錯誤是 Interop 的常見問題之一，這些處理常式是用來處理 COM 物件引發的事件。  這種錯誤會被忽略，除非您使用 `On Error` 或 `Try...Catch...Finally` 陳述式特別檢查錯誤。  例如，下列範例是來自具有 Microsoft ActiveX Data Objects 2.8 Library COM 物件之參考的 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] 專案。  
  
 [!code-vb[VbVbalrInterop#24](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 這個範例如預期的引發錯誤。  然而，如果您嘗試在不使用 `Try...Catch...Finally` 區塊的情況下使用相同範例，則會忽略這個錯誤，就像您使用 `OnError Resume Next` 陳述式一般。  若沒有錯誤處理，則除以零會無訊息地失敗。  因為這個錯誤永遠不會引發未處理的例外狀況錯誤，您必須在處理 COM 物件事件的事件處理常式中使用某種形式的例外狀況處理。  
  
### 認識 COM Interop 錯誤  
 若沒有處理錯誤，Interop 呼叫產生的錯誤通常只能提供少量的資訊。  當問題發生時，請盡可能使用結構化的錯誤處理方式，提供更多問題相關資訊。  這在偵錯應用程式時特別有用，  例如：  
  
 [!code-vb[VbVbalrInterop#25](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 您可以藉由檢查例外狀況物件的內容，找出錯誤描述、HRESULT 和 COM 錯誤來源之類的資訊。  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a> ActiveX 控制項問題  
 大部分與 Visual Basic 6.0 搭配使用的 ActiveX 控制項都能夠與 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] 搭配使用，而不會發生問題。  主要的例外狀況是容器控制項或視覺上包含其他控制項的控制項。  一些在 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 中無法正確運作的舊版控制項範例如下：  
  
-   Microsoft Forms 2.0 框架控制項  
  
-   上下按鈕控制項，也稱為微調控制項  
  
-   Sheridan 索引標籤控制項  
  
 對未支援的 ActiveX 控制項問題只有一些替代方法。  如果您有原始來源程式碼，則可將現有的控制項轉換為 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 的控制項。  或者，您可以向軟體廠商洽詢更新的控制項 .NET 相容版，以取代未支援的 ActiveX 控制項。  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a> 傳遞控制項 ByRef 的 ReadOnly 屬性  
 當您將一些舊版 ActiveX 控制項的 `ReadOnly` 屬性當做 `ByRef` 參數傳遞至其他程序時，[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] 有時會引發 COM 錯誤，如 "Error 0x800A017F CTL\_E\_SETNOTSUPPORTED"。  Visual Basic 6.0 中類似的程序呼叫不會引發錯誤，並視同您用傳值 \(By Value\) 的方式傳遞參數。  您在 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] 中看到的錯誤訊息是 COM 物件，這個物件報告您嘗試改變沒有屬性 `Set` 程序的屬性。  
  
 如果您可以存取正在呼叫的程序，便可以使用 `ByVal` 關鍵字宣告接受 `ReadOnly` 屬性的參數，來防止這個錯誤的發生。  例如：  
  
 [!code-vb[VbVbalrInterop#26](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 如果您不具有被呼叫程序的來源程式碼的存取權限，您可以經由在呼叫程序外新增一組額外的括號，來強制用傳值的方式傳遞屬性。  例如，在具有 Microsoft ActiveX Data Objects 2.8 Library COM 物件之參考的專案中，可以使用：  
  
 [!code-vb[VbVbalrInterop#27](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a> 部署公開 Interop 的組件  
 部署公開 COM 介面的組件會引發一些特殊的問題。  例如，當個別的應用程式參考相同的 COM 組件時會發生潛在的問題。  當安裝了新版本的組件，而其他應用程式仍然使用舊版本的組件時，常會發生這種情況。  解除安裝共用 DLL 檔的組件時，會無意間造成其他組件無法使用該解除安裝的組件。  
  
 若要避免這個問題，應該將共用的組件安裝到全域組件快取 \(GAC\)，並對為該元件使用 MergeModule。  如果無法在 GAC 中安裝應用程式，就應該將其安裝在版本特定子目錄中的 CommonFilesFolder 中。  
  
 未共用的組件應該和呼叫應用程式並列放置在目錄中。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [Tlbexp.exe \(Type Library Exporter\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md)   
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [全域組件快取](../Topic/Global%20Assembly%20Cache.md)