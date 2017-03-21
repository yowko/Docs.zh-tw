---
title: "/link (Visual Basic) |Microsoft 文件"
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
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: e98c855f0a0185e9d1b6682df9fc734e9f1f07bc
ms.lasthandoff: 03/13/2017

---
# <a name="link-visual-basic"></a>/link (Visual Basic)
會導致編譯器允許您目前正在編譯的專案使用指定的組件中的 COM 型別資訊。  
  
## <a name="syntax"></a>語法  
  
```  
/link:fileList  
' -or-  
/l:fileList  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`fileList`|必要項。 組件檔案名稱的逗號分隔清單。 如果檔案名稱包含空格，請用引號括住名稱。|  
  
## <a name="remarks"></a>備註  
 `/link`選項可讓您部署應用程式包含內嵌類型資訊。 應用程式可以使用執行階段組件中實作的內嵌的類型資訊而不需要執行階段組件的參考的型別。 如果發佈各種執行階段組件版本，包含內嵌的類型資訊的應用程式可以使用的各種版本而不必重新編譯。 如需範例，請參閱[逐步解說︰ 從 Managed 組件的內嵌類型](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)。  
  
 使用`/link`選項在您正在使用 COM interop 時會特別有用。 您可以內嵌 COM 型別，使您的應用程式不再需要的主要 interop 組件 (PIA) 在目標電腦上。 `/link`選項會指示編譯器將內嵌從參考的 interop 組件至產生的編譯程式碼的 COM 型別資訊。 COM 類型的 CLSID (GUID) 值來識別。 如此一來，您的應用程式可以在已安裝相同的 COM 型別使用相同的 CLSID 值的目標電腦上執行。 Microsoft Office 自動化的應用程式都很好的例子。 等 Office 應用程式通常會保留在不同版本的相同 CLSID 值，因為您的應用程式可以使用參照的 COM 型別，在目標電腦上安裝.NET Framework 4 或更新版本的長時間以及應用程式所使用的方法、 屬性或事件，會包含在參照 COM 型別。  
  
 `/link`選項嵌入介面、 結構和委派。 不支援內嵌 COM 類別。  
  
> [!NOTE]
>  當您在程式碼中建立內嵌的 COM 型別的執行個體時，您必須使用適當的介面來建立執行個體。 嘗試建立內嵌的 COM 型別的執行個體使用 CoClass 導致的錯誤。  
  
 若要設定`/link`選項[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]、 加入組件參考和設定`Embed Interop Types`屬性**true**。 預設值為`Embed Interop Types`屬性是**false**。  
  
 如果您連結至 COM 組件 （A） 其本身參考另一個 COM 組件 (組件 B)，您也必須連結到 B 組件，如果下列其中一種︰  
  
-   來自組件 A 的型別繼承自型別或實作介面從 b 組件  
  
-   欄位、 屬性、 事件或方法，從組件 B 的傳回型別或參數型別會叫用。  
  
 使用[/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)指定一或多個組件參考所在的目錄。  
  
 像[/參考](../../../visual-basic/reference/command-line-compiler/reference.md)編譯器選項`/link`編譯器選項會使用參考常用 Vbc.rsp 回應檔[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件。 使用[/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)若不想讓編譯器使用 Vbc.rsp 檔的編譯器選項。  
  
 簡短形式`/link`是`/l`。  
  
## <a name="generics-and-embedded-types"></a>泛型和內嵌的類型  
 下列章節將說明在內嵌 interop 類型的應用程式中使用泛型型別限制。  
  
### <a name="generic-interfaces"></a>泛型介面  
 無法使用內嵌的 interop 組件的泛型介面。 這在下列範例中顯示。  
  
 [!code-vb[VbLinkCompiler #&1;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a>具有泛型參數型別  
 具有泛型參數的型別內嵌的 interop 組件的類型無法使用如果類型是從外部組件。 這項限制不適用於介面。 例如，假設<xref:Microsoft.Office.Interop.Excel.Range>中所定義的介面<xref:Microsoft.Office.Interop.Excel>組件。</xref:Microsoft.Office.Interop.Excel> </xref:Microsoft.Office.Interop.Excel.Range> 如果文件庫內嵌 interop 類型從<xref:Microsoft.Office.Interop.Excel>組件和型別傳回泛型型別參數的方法是的公開<xref:Microsoft.Office.Interop.Excel.Range>介面，方法必須傳回泛型介面，如下列程式碼範例所示。</xref:Microsoft.Office.Interop.Excel.Range> </xref:Microsoft.Office.Interop.Excel>  
  
 [!code-vb[VbLinkCompiler #&2;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler #&3;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler #&4;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 在下列範例中，用戶端程式碼可以呼叫這個方法會傳回<xref:System.Collections.IList>泛型介面不會發生錯誤。</xref:System.Collections.IList>  
  
 [!code-vb[VbLinkCompiler #&5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a>範例  
 下列程式碼會編譯原始程式檔`OfficeApp.vb`參考組件從`COMData1.dll`和`COMData2.dll`產生`OfficeApp.exe`。  
  
```vb  
vbc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [逐步解說︰ 內嵌 Managed 組件的類型](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)   
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [/ 未設定](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [COM Interop 簡介](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
