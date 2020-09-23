---
title: 疑難排解互通性的問題
ms.date: 07/20/2015
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
ms.openlocfilehash: 135b121638b92adc5a3b0920aa29d10fd1d62d14
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075989"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>疑難排解互通性 (Visual Basic)

當您在 COM 和 .NET Framework 的 managed 程式碼之間交互操作時，您可能會遇到下列一或多個常見的問題。  
  
## <a name="interop-marshaling"></a><a name="vbconinteroperabilitymarshalinganchor1"></a> Interop 封送處理  

 有時，您可能必須使用不屬於 .NET Framework 的資料類型。 Interop 元件會處理 COM 物件的大部分工作，但是您可能必須控制在 managed 物件公開至 COM 時所使用的資料類型。 例如，類別庫中的結構必須 `BStr` 在傳送給 Visual Basic 6.0 和較早版本所建立之 COM 物件的字串上指定非受控型別。 在這種情況下，您可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，使 managed 類型公開為非受控類型。  
  
## <a name="exporting-fixed-length-strings-to-unmanaged-code"></a><a name="vbconinteroperabilitymarshalinganchor2"></a> 將固定長度的字串匯出至非受控碼  

 在 Visual Basic 6.0 及更早版本中，字串會以不含 null 終止字元的位元組序列形式匯出至 COM 物件。 為了與其他語言相容，Visual Basic .NET 會在匯出字串時包含終止字元。 解決此不相容性的最佳方式，是將缺少終止字元的字串匯出為或的陣列 `Byte` `Char` 。  
  
## <a name="exporting-inheritance-hierarchies"></a><a name="vbconinteroperabilitymarshalinganchor3"></a> 正在匯出繼承階層  

 Managed 類別階層會在公開為 COM 物件時壓平合併。 例如，如果您定義具有成員的基類，然後在公開為 COM 物件的衍生類別中繼承基類，則在 COM 物件中使用衍生類別的用戶端將無法使用繼承的成員。 基類成員只能從 COM 物件存取為基類的實例，而且只有在基類也建立為 COM 物件時才可存取。  
  
## <a name="overloaded-methods"></a>多載方法  

 雖然您可以使用 Visual Basic 建立多載的方法，但 COM 並不支援它們。 當包含多載方法的類別公開為 COM 物件時，會為多載方法產生新的方法名稱。  
  
 例如，假設有一個類別具有兩個方法的多載 `Synch` 。 當類別公開為 COM 物件時，新產生的方法名稱可能是 `Synch` 和 `Synch_2` 。  
  
 重新命名可能會對 COM 物件的取用者造成兩個問題。  
  
1. 用戶端可能不會預期產生的方法名稱。  
  
2. 當新的多載加入至類別或其基類時，公開為 COM 物件的類別中所產生的方法名稱可能會變更。 這可能會導致版本控制問題。  
  
 若要解決這兩個問題，請在開發將公開為 COM 物件的物件時，為每個方法提供唯一的名稱，而非使用多載。  
  
## <a name="use-of-com-objects-through-interop-assemblies"></a><a name="vbconinteroperabilitymarshalinganchor4"></a> 透過 Interop 元件使用 COM 物件  

 您可以使用 interop 元件，就像是它們所代表之 COM 物件的 managed 程式碼取代一樣。 不過，由於它們是包裝函式，而不是實際的 COM 物件，因此使用 interop 元件和標準元件之間有一些差異。 這些差異區域包括類別的公開，以及參數和傳回值的資料類型。  
  
## <a name="classes-exposed-as-both-interfaces-and-classes"></a><a name="vbconinteroperabilitymarshalinganchor5"></a> 公開為介面和類別的類別  

 不同于標準元件中的類別，COM 類別會在 interop 元件中公開為介面和表示 COM 類別的類別。 介面的名稱與 COM 類別的名稱相同。 Interop 類別的名稱與原始 COM 類別的名稱相同，但附加了 "Class" 這個字。 例如，假設您有一個具有 COM 物件之 interop 元件參考的專案。 如果 COM 類別命名為 `MyComClass` ，IntelliSense 和物件瀏覽器會顯示名為的介面， `MyComClass` 以及名為的類別 `MyComClassClass` 。  
  
## <a name="creating-instances-of-a-net-framework-class"></a><a name="vbconinteroperabilitymarshalinganchor6"></a> 建立 .NET Framework 類別的實例  

 一般來說，您會使用具有類別名稱的語句來建立 .NET Framework 類別的實例 `New` 。 具有 interop 元件表示的 COM 類別，是您可以使用語句搭配介面的一種情況 `New` 。 除非您使用 COM 類別搭配 `Inherits` 語句，否則您可以使用介面，就像使用類別一樣。 下列程式碼示範如何 `Command` 在專案中建立物件，該物件具有 Microsoft ActiveX Data Objects 2.8 程式庫 COM 物件的參考：  
  
 [!code-vb[VbVbalrInterop#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#20)]  
  
 但是，如果您使用 COM 類別做為衍生類別的基底，您必須使用表示 COM 類別的 interop 類別，如下列程式碼所示：  
  
 [!code-vb[VbVbalrInterop#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#21)]  
  
> [!NOTE]
> Interop 元件會隱含地執行表示 COM 類別的介面。 您不應該嘗試使用 `Implements` 語句來執行這些介面，否則就會產生錯誤。  
  
## <a name="data-types-for-parameters-and-return-values"></a><a name="vbconinteroperabilitymarshalinganchor7"></a> 參數和傳回值的資料類型  

 不同于標準元件的成員，interop 元件成員的資料類型可能與原始物件宣告中所用的不同。 雖然 interop 元件會以隱含方式將 COM 類型轉換成相容的 common language runtime 型別，但是您應該注意這兩個邊所使用的資料類型，以防止執行階段錯誤。 例如，在 Visual Basic 6.0 和較早版本所建立的 COM 物件中，型別的值會 `Integer` 假設 .NET Framework 對等型別 `Short` 。 建議您在使用匯入的成員之前，先使用物件瀏覽器來檢查其特性。  
  
## <a name="module-level-com-methods"></a><a name="vbconinteroperabilitymarshalinganchor8"></a> 模組層級 COM 方法  

 大部分 COM 物件的使用方式是使用關鍵字來建立 COM 類別的實例 `New` ，然後呼叫物件的方法。 這項規則的例外狀況包括包含 `AppObj` 或 com 類別的 com 物件 `GlobalMultiUse` 。 這類類別與 Visual Basic .NET 類別中的模組層級方法類似。 當您第一次呼叫其中一個方法時，Visual Basic 6.0 及更早版本會隱含地為您建立這類物件的實例。 例如，在 Visual Basic 6.0 中，您可以新增 Microsoft DAO 3.6 物件程式庫的參考，並呼叫 `DBEngine` 方法，而不需要先建立實例：  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET 需要您一律先建立 COM 物件的實例，才能使用其方法。 若要在 Visual Basic 中使用這些方法，請宣告所需類別的變數，並使用 new 關鍵字將物件指派給物件變數。 `Shared`當您想要確保只建立類別的一個實例時，可以使用關鍵字。  
  
 [!code-vb[VbVbalrInterop#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#23)]  
  
## <a name="unhandled-errors-in-event-handlers"></a><a name="vbconinteroperabilitymarshalinganchor9"></a> 事件處理常式中的未處理錯誤  

 其中一個常見的 interop 問題牽涉到事件處理常式中的錯誤，這些錯誤會處理 COM 物件所引發的事件。 除非您使用或語句來明確檢查錯誤，否則會忽略這類錯誤 `On Error` `Try...Catch...Finally` 。 例如，下列範例是來自具有 Microsoft ActiveX Data Objects 2.8 程式庫 COM 物件參考的 Visual Basic .NET 專案。  
  
 [!code-vb[VbVbalrInterop#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#24)]  
  
 此範例會如預期般引發錯誤。 但是，如果您在沒有區塊的情況下嘗試相同的範例 `Try...Catch...Finally` ，就會忽略此錯誤，就像您使用 `OnError Resume Next` 語句一樣。 如果沒有錯誤處理，則零除的無訊息模式會失敗。 因為這類錯誤永遠不會引發未處理的例外狀況錯誤，所以請務必在處理來自 COM 物件之事件的事件處理常式中，使用某種形式的例外狀況處理。  
  
### <a name="understanding-com-interop-errors"></a>瞭解 COM interop 錯誤  

 如果沒有錯誤處理，interop 呼叫通常會產生錯誤，提供少量的資訊。 可能的話，請使用結構化錯誤處理來提供問題發生時的詳細資訊。 當您對應用程式進行偵錯工具時，這會特別有用。 例如：  
  
 [!code-vb[VbVbalrInterop#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#25)]  
  
 您可以藉由檢查例外狀況物件的內容，找到錯誤描述、HRESULT 和 COM 錯誤來源的資訊。  
  
## <a name="activex-control-issues"></a><a name="vbconinteroperabilitymarshalinganchor10"></a> ActiveX 控制項問題  

 大部分適用于 Visual Basic 6.0 的 ActiveX 控制項都能搭配 Visual Basic 的 .NET 運作，而不會發生問題。 主要的例外狀況是容器控制項，或是以視覺化方式包含其他控制項的控制項。 某些較舊的控制項範例無法搭配 Visual Studio 正確運作，如下所示：  
  
- Microsoft Forms 2.0 框架控制項  
  
- 由上而下的控制項（也稱為微調控制項）  
  
- Sheridan 索引標籤控制項  
  
 針對不支援的 ActiveX 控制項問題，只有一些因應措施。 如果您擁有原始原始程式碼，您可以將現有的控制項遷移至 Visual Studio。 否則，您可以向軟體廠商確認是否已更新。用來取代不支援的 ActiveX 控制項之控制項的 .NET 相容版本。  
  
## <a name="passing-readonly-properties-of-controls-byref"></a><a name="vbconinteroperabilitymarshalinganchor11"></a> 傳遞控制項的 ReadOnly 屬性 ByRef  

 當您將 `ReadOnly` 某些舊版 ActiveX 控制項的屬性傳遞至其他程式的參數時，Visual Basic .net 有時會引發 COM 錯誤，例如「錯誤 0x800A017F CTL_E_SETNOTSUPPORTED」 `ByRef` 。 從 Visual Basic 6.0 的類似程序呼叫不會引發錯誤，而且會將參數視為您以傳值方式傳遞。 Visual Basic .NET 錯誤訊息指出您嘗試變更的屬性沒有屬性程式 `Set` 。  
  
 如果您可以存取所呼叫的程式，您可以使用 `ByVal` 關鍵字來宣告接受屬性的參數，以避免此錯誤 `ReadOnly` 。 例如：  
  
 [!code-vb[VbVbalrInterop#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#26)]  
  
 如果您無法存取所呼叫之程式的原始程式碼，您可以在呼叫程式前後加上一組額外的括弧，以強制以傳值方式傳遞屬性。 例如，在具有 Microsoft ActiveX Data Objects 2.8 程式庫 COM 物件參考的專案中，您可以使用：  
  
 [!code-vb[VbVbalrInterop#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#27)]  
  
## <a name="deploying-assemblies-that-expose-interop"></a><a name="vbconinteroperabilitymarshalinganchor12"></a> 部署公開 Interop 的元件  

 部署公開 COM 介面的元件會帶來一些獨特的挑戰。 例如，當不同的應用程式參考相同的 COM 元件時，就會發生潛在問題。 當安裝新版本的元件，而另一個應用程式仍在使用舊版元件時，就會發生這種情況。 如果您卸載共用 DLL 的元件，您可以不小心讓其他元件無法使用它。  
  
 若要避免這個問題，您應該將共用的元件安裝到全域組件快取 (GAC) 並使用元件的 MergeModule。 如果您無法在 GAC 中安裝應用程式，則應該將它安裝到 CommonFilesFolder 的版本特定子目錄中。  
  
 未共用的元件應該在具有呼叫應用程式的目錄中並存。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [COM Interop](index.md)
- [Tlbimp.exe (類型程式庫匯入工具)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (類型程式庫匯出工具)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [逐步解說：實作 COM 物件的繼承](walkthrough-implementing-inheritance-with-com-objects.md)
- [Inherits Statement](../../language-reference/statements/inherits-statement.md)
- [全域組件快取](../../../framework/app-domains/gac.md)
