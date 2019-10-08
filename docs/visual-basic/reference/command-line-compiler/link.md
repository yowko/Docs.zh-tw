---
title: -link （Visual Basic）
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: e131b39e05badf0bb90fbbb14761571003156f85
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005520"
---
# <a name="-link-visual-basic"></a>-link （Visual Basic）
讓編譯器將所指定組件的 COM 類型資訊全部提供給您目前編譯的專案。  
  
## <a name="syntax"></a>語法  
  
```console  
-link:fileList  
```

或  

```console
-l:fileList  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`fileList`|必要項。 以逗號分隔的組件檔案名稱清單。 如果檔案名稱包含空格，請用引號括住名稱。|  
  
## <a name="remarks"></a>備註  
 `-link` 選項可讓您部署具有內嵌類型資訊的應用程式。 應用程式接著可以使用執行階段組件中實作內嵌類型資訊的類型，而不需要參考執行階段組件。 如果執行階段組件有許多發行版本，包含內嵌類型資訊的應用程式不需要重新編譯，就可以搭配各種版本使用。 如需範例，請參閱[逐步解說：從 Managed 組件內嵌類型](../../../standard/assembly/embed-types-visual-studio.md)。  
  
 如果您正在使用 COM Interop，使用 `-link` 選項會特別有用。 您可以內嵌 COM 類型，如此一來您的應用程式就不會再要求目標電腦上必須有主要 Interop 組件 (PIA)。 `-link` 選項會指示編譯器將所參考 Interop 組件的 COM 類型資訊嵌入編譯產生的程式碼。 COM 類型是由 CLSID (GUID) 值來識別。 因此，應用程式可以在已安裝含相同 CLSID 值之相同 COM 類型的目標電腦上執行。 自動化 Microsoft Office 的應用程式即為一個很好的例子。 由於 Office 等應用程式通常會在不同版本間保持相同的 CLSID 值，因此只要目標電腦上已安裝 .NET Framework 4 或更新版本，且應用程式使用包含在所參考 COM 類型中的方法、屬性或事件，應用程式就可以使用這些參考的 COM 類型。  
  
 `-link` 選項只能內嵌介面、結構和委派。 不支援內嵌 COM 類別。  
  
> [!NOTE]
> 當您在程式碼中建立內嵌 COM 類型的執行個體時，必須使用適當的介面來建立執行個體。 嘗試使用 CoClass 建立內嵌 COM 類型的執行個體將會導致錯誤。  
  
 若要在 Visual Studio 中設定 `-link` 選項，請新增組件參考，並將 `Embed Interop Types` 屬性設定為 **true**。 `Embed Interop Types` 屬性的預設值為 **false**。  
  
 如果您所連結的 COM 組件 (A) 本身參考另一個 COM 組件 (組件 B)，您也必須在發生下列任一情況時連結到 B 組件：  
  
- 組件 A 的類型繼承自組件 B 的類型，或是實作組件 B 的介面。  
  
- 所叫用的欄位、屬性、事件或方法具有組件 B 的傳回型別或參數類型。  
  
 請使用[-libpath](libpath.md)來指定您的一或多個元件參考所在的目錄。  
  
 如同[/reference](reference.md)編譯器選項，`-link` 編譯器選項會使用 Vbc 回應檔，該檔案會參考常用 .NET Framework 元件。 如果您不想要編譯器使用 Vbc .rsp 檔案，請使用[-noconfig](noconfig.md)編譯器選項。  
  
 `-link` 的簡短形式為 `-l`。  
  
## <a name="generics-and-embedded-types"></a>泛型和內嵌類型  
 下列各節說明在內嵌 Interop 類型的應用程式中使用泛型型別時的限制。  
  
### <a name="generic-interfaces"></a>泛型介面  
 無法使用從 Interop 組件內嵌的泛型介面。 這在下列範例中顯示。  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a>具有泛型參數的類型  
 如果具有泛型參數的類型來自外部組件，且其參數的類型是從 Interop 組件內嵌的，則無法使用該類型。 這項限制不適用於介面。 例如，請考慮使用 <xref:Microsoft.Office.Interop.Excel> 組件中所定義的 <xref:Microsoft.Office.Interop.Excel.Range> 介面。 如果程式庫內嵌來自 <xref:Microsoft.Office.Interop.Excel> 組件的 Interop 類型，並公開傳回泛型型別的方法，但是此泛型型別具有類型為 <xref:Microsoft.Office.Interop.Excel.Range> 介面的參數，則該方法就必須傳回泛型介面，如下列程式碼範例所示。  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 在下列範例中，用戶端程式碼可以呼叫傳回 <xref:System.Collections.IList> 泛型介面的方法，且不會發生錯誤。  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a>範例  
 下列命令列會從 `COMData1.dll` 和 `COMData2.dll` 編譯原始程式檔 @no__t 0 和參考元件，以產生 `OfficeApp.exe`。  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [逐步解說：從受控組件內嵌類型](../../../standard/assembly/embed-types-visual-studio.md)
- [-reference （Visual Basic）](reference.md)
- [-noconfig](noconfig.md)
- [-libpath](libpath.md)
- [編譯命令列範例](sample-compilation-command-lines.md)
- [COM Interop 簡介](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
