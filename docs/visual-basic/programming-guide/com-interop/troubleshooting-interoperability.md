---
title: 疑難排解互通性 (Visual Basic)
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
ms.openlocfilehash: c04cd0928eb83aabcd1f0f4b1b43f8ae6d356d20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969329"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>疑難排解互通性 (Visual Basic)
當您在 COM 與 .NET Framework 的 managed 程式碼之間交互操作時, 您可能會遇到下列一個或多個常見的問題。  
  
## <a name="vbconinteroperabilitymarshalinganchor1"></a>Interop 封送處理  
 有時候, 您可能必須使用不屬於 .NET Framework 的資料類型。 Interop 元件會處理 COM 物件的大部分工作, 但您可能必須控制將 managed 物件公開給 COM 時所使用的資料類型。 例如, 類別庫中的結構必須在傳送`BStr`至 Visual Basic 6.0 和更早版本所建立之 COM 物件的字串上, 指定非受控型別。 在這種情況下, 您可以<xref:System.Runtime.InteropServices.MarshalAsAttribute>使用屬性, 使 managed 類型公開為非受控類型。  
  
## <a name="vbconinteroperabilitymarshalinganchor2"></a>將固定長度的字串匯出至未受管理的程式碼  
 在 Visual Basic 6.0 和更早版本中, 字串會以不含 null 終止字元的位元組序列形式匯出至 COM 物件。 為了與其他語言相容, 在匯出字串時, Visual Basic .NET 會包含一個終止字元。 解決此不相容性的最佳方式, 是將缺少終止字元的字串匯出為或`Byte` `Char`的陣列。  
  
## <a name="vbconinteroperabilitymarshalinganchor3"></a>匯出繼承階層  
 當公開為 COM 物件時, Managed 類別階層會壓平合併。 例如, 如果您使用成員定義基類, 然後繼承衍生類別中公開為 COM 物件的基類, 則在 COM 物件中使用衍生類別的用戶端將無法使用繼承的成員。 基類成員只能從 COM 物件存取為基類的實例, 而且只有在基類也建立為 COM 物件時才可以。  
  
## <a name="overloaded-methods"></a>多載的方法  
 雖然您可以使用 Visual Basic 建立多載的方法, 但 COM 並不支援它們。 當包含多載方法的類別公開為 COM 物件時, 會為多載的方法產生新的方法名稱。  
  
 例如, 假設有一個類別具有`Synch`方法的兩個多載。 當類別公開為 COM 物件時, 新產生的方法名稱可能是`Synch`和。 `Synch_2`  
  
 重新命名可能會對 COM 物件的取用者造成兩個問題。  
  
1. 用戶端可能不會預期產生的方法名稱。  
  
2. 將新的多載新增至類別或其基類時, 在公開為 COM 物件的類別中產生的方法名稱可能會變更。 這可能會造成版本控制問題。  
  
 若要解決這兩個問題, 當您開發將公開為 COM 物件的物件時, 請為每個方法提供唯一的名稱, 而不是使用多載。  
  
## <a name="vbconinteroperabilitymarshalinganchor4"></a>透過 Interop 元件使用 COM 物件  
 Interop 元件的使用方式幾乎就像是它們所代表 COM 物件的 managed 程式碼取代。 不過, 因為它們是包裝函式, 而不是實際的 COM 物件, 所以使用 interop 元件和標準元件之間有一些差異。 這些差異區域包括類別的公開, 以及參數和傳回值的資料類型。  
  
## <a name="vbconinteroperabilitymarshalinganchor5"></a>公開為介面和類別的類別  
 不同于標準元件中的類別, COM 類別會在 interop 元件中公開為介面和代表 COM 類別的類別。 介面的名稱與 COM 類別的名稱相同。 Interop 類別的名稱與原始 COM 類別的名稱相同, 但附加了 "Class" 這個字。 例如, 假設您有一個專案, 其中包含 COM 物件的 interop 元件參考。 如果 COM 類別名`MyComClass`為, IntelliSense 和物件瀏覽器會顯示名為`MyComClass`的介面和名為`MyComClassClass`的類別。  
  
## <a name="vbconinteroperabilitymarshalinganchor6"></a>建立 .NET Framework 類別的實例  
 一般來說, 您會使用具有類別名稱的`New`語句來建立 .NET Framework 類別的實例。 以 interop 元件表示的 COM 類別, 是您可以在介面中使用`New`語句的一種情況。 除非您使用 COM 類別`Inherits`搭配語句, 否則您可以使用介面, 就像類別一樣。 下列程式碼示範如何在具有 Microsoft `Command` ActiveX Data Objects 2.8 程式庫 COM 物件參考的專案中建立物件:  
  
 [!code-vb[VbVbalrInterop#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#20)]  
  
 不過, 如果您使用 COM 類別做為衍生類別的基底, 則必須使用代表 COM 類別的 interop 類別, 如下列程式碼所示:  
  
 [!code-vb[VbVbalrInterop#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#21)]  
  
> [!NOTE]
> Interop 元件會隱含地執行代表 COM 類別的介面。 您不應該嘗試使用`Implements`語句來執行這些介面, 否則會產生錯誤。  
  
## <a name="vbconinteroperabilitymarshalinganchor7"></a>參數和傳回值的資料類型  
 不同于標準元件的成員, interop 元件成員可能會有與原始物件宣告中使用的不同的資料類型。 雖然 interop 元件會隱含地將 COM 類型轉換成相容的 common language runtime 類型, 但您應該注意雙方所使用的資料類型, 以避免執行階段錯誤。 例如, 在 Visual Basic 6.0 和更早版本中建立的 COM 物件中, 類型`Integer`的值會假設 .NET Framework 對`Short`等類型。 建議您在使用匯入的成員之前, 先使用物件瀏覽器來檢查其特性。  
  
## <a name="vbconinteroperabilitymarshalinganchor8"></a>模組層級 COM 方法  
 大部分 com 物件的使用方式, 是使用`New`關鍵字來建立 COM 類別的實例, 然後呼叫物件的方法。 此規則有一個例外, 包括包含`AppObj`或`GlobalMultiUse` com 類別的 com 物件。 這類類別與 Visual Basic .NET 類別中的模組層級方法類似。 Visual Basic 6.0 和舊版版本會在您第一次呼叫其中一個方法時, 隱含地為您建立這類物件的實例。 例如, 在 Visual Basic 6.0 中, 您可以將參考新增至 Microsoft DAO 3.6 物件程式庫, 並呼叫`DBEngine`方法, 而不需要先建立實例:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET 要求您一定要先建立 COM 物件的實例, 才能使用其方法。 若要在 Visual Basic 中使用這些方法, 請宣告所需類別的變數, 並使用 new 關鍵字將物件指派給物件變數。 當`Shared`您想要確保只會建立類別的一個實例時, 可以使用關鍵字。  
  
 [!code-vb[VbVbalrInterop#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#23)]  
  
## <a name="vbconinteroperabilitymarshalinganchor9"></a>事件處理常式中的未處理錯誤  
 其中一個常見的 interop 問題牽涉到處理 COM 物件所引發之事件的事件處理常式中的錯誤。 除非您使用`On Error`或`Try...Catch...Finally`語句來特別檢查錯誤, 否則會忽略這類錯誤。 例如, 下列範例來自具有 Microsoft ActiveX Data Objects 2.8 程式庫 COM 物件參考的 Visual Basic .NET 專案。  
  
 [!code-vb[VbVbalrInterop#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#24)]  
  
 這個範例會如預期般引發錯誤。 不過, 如果您嘗試相同的範例, 但`Try...Catch...Finally`沒有區塊, 則會忽略此錯誤, 就如同`OnError Resume Next`您使用語句一樣。 如果沒有錯誤處理, 則零除的無訊息失敗。 由於這類錯誤永遠不會引發未處理的例外狀況錯誤, 因此在處理 COM 物件事件的事件處理常式中, 請務必使用某種形式的例外狀況處理。  
  
### <a name="understanding-com-interop-errors"></a>瞭解 COM Interop 錯誤  
 如果沒有錯誤處理, interop 呼叫通常會產生錯誤, 而不會提供一些資訊。 可能的話, 請使用結構化錯誤處理來提供發生問題時的詳細資訊。 當您在偵錯工具時, 這會特別有用。 例如：  
  
 [!code-vb[VbVbalrInterop#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#25)]  
  
 您可以藉由檢查 exception 物件的內容, 來尋找如錯誤描述、HRESULT 和 COM 錯誤來源的資訊。  
  
## <a name="vbconinteroperabilitymarshalinganchor10"></a>ActiveX 控制項問題  
 大部分與 Visual Basic 6.0 搭配使用的 ActiveX 控制項都能與 Visual Basic .NET 搭配使用, 而不會發生問題。 主要的例外狀況包括容器控制項, 或以視覺化方式包含其他控制項的控制項。 某些較舊的控制項範例無法與 Visual Studio 正確搭配運作, 如下所示:  
  
- Microsoft Forms 2.0 框架控制項  
  
- 上下按鈕控制項, 也稱為微調控制項  
  
- Sheridan 索引標籤控制項  
  
 針對不支援的 ActiveX 控制項問題, 只有一些因應措施。 如果您擁有原始的原始程式碼, 您可以將現有的控制項遷移至 Visual Studio。 否則, 您可以向軟體廠商確認是否已更新。控制項的 NET 相容版本, 用來取代不支援的 ActiveX 控制項。  
  
## <a name="vbconinteroperabilitymarshalinganchor11"></a>傳遞控制項的 ReadOnly 屬性 ByRef  
 當您將一些較舊的 ActiveX `ReadOnly` `ByRef`控制項的屬性當做參數傳遞至其他程式時, Visual Basic .net 有時會引發 COM 錯誤, 例如「錯誤 0x800A017F CTL_E_SETNOTSUPPORTED」。 來自 Visual Basic 6.0 的類似程式呼叫不會引發錯誤, 而且會將參數視為以傳值方式傳遞。 Visual Basic 的 .net 錯誤訊息指出您嘗試變更沒有屬性`Set`程式的屬性。  
  
 如果您有權存取所呼叫的程式, 您可以使用`ByVal`關鍵字宣告接受`ReadOnly`屬性的參數, 以避免這個錯誤。 例如：  
  
 [!code-vb[VbVbalrInterop#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#26)]  
  
 如果您無法存取所呼叫程式的原始程式碼, 您可以在呼叫程式前後新增一組額外的括弧, 以強制以傳值方式傳遞屬性。 例如, 在具有 Microsoft ActiveX Data Objects 2.8 程式庫 COM 物件參考的專案中, 您可以使用:  
  
 [!code-vb[VbVbalrInterop#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#27)]  
  
## <a name="vbconinteroperabilitymarshalinganchor12"></a>部署公開 Interop 的元件  
 部署公開 COM 介面的元件會帶來一些獨特的挑戰。 例如, 當不同的應用程式參考相同的 COM 元件時, 可能會發生問題。 當安裝新版本的元件, 而且另一個應用程式仍在使用舊版的元件時, 就會發生這種情況。 如果您卸載共用 DLL 的元件, 就可以不小心讓其他元件無法使用它。  
  
 若要避免這個問題, 您應該將共用元件安裝到全域組件快取 (GAC), 並使用元件的合併模組。 如果您無法將應用程式安裝在 GAC 中, 則應該將它安裝在特定版本子目錄中的 CommonFilesFolder。  
  
 未共用的元件應該與呼叫應用程式位於目錄中的並存位置。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (類型程式庫匯入工具)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (類型程式庫匯出工具)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [逐步解說：實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [全域組件快取](../../../framework/app-domains/gac.md)
