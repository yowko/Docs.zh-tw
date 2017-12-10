---
title: "常見屬性 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f536d4c420f24241a4b5f36094dad2f6c335f1d6
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="common-attributes-visual-basic"></a>常見屬性 (Visual Basic)
本主題說明在 Visual Basic 程式中最常用的屬性。  
  
-   [全域屬性](#Global)  
  
-   [Obsolete 屬性](#Obsolete)  
  
-   [條件式屬性](#Conditional)  
  
-   [呼叫端資訊屬性](#CallerInfo)  
  
-   [Visual Basic 屬性](#VB)  
  
##  <a name="Global"></a> 全域屬性  
 大部分屬性會套用至特定語言項目 (例如類別或方法)；不過，有些屬性是全域屬性，其套用至整個組件或模組。 例如，<xref:System.Reflection.AssemblyVersionAttribute> 屬性可以用來將版本資訊內嵌到組件，與下面類似：  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 之後，任何全域屬性會出現在原始碼最上層`Imports`陳述式之前的任何類型、 模組或命名空間宣告。 全域屬性可以出現在多個原始程式檔中，但必須使用單一編譯階段編譯檔案。 Visual Basic 專案中，通常會處於 AssemblyInfo.vb 檔案 （檔案時自動建立 Visual Studio 中建立的專案） 的全域屬性。  
  
 組件屬性是提供組件相關資訊的值。 它們的分類如下：  
  
-   組件識別屬性  
  
-   資訊屬性  
  
-   組件資訊清單屬性  
  
### <a name="assembly-identity-attributes"></a>組件識別屬性  
 三個具有強式名稱 (如果適用) 的屬性會判斷組件的識別：名稱、版本與文化特性。 這些屬性會形成組件的完整名稱，且在程式碼中參考組件時需要用到。 您可以使用屬性來設定組件的版本和文化特性。 不過，名稱值乃是根據包含組件資訊清單的檔案來由編譯器、[組件資訊對話方塊](/visualstudio/ide/reference/assembly-information-dialog-box) 中的 Visual Studio IDE 或在建立組件時的組件連結器 (Al.exe) 所設定。 <xref:System.Reflection.AssemblyFlagsAttribute> 屬性指定組件的多個複本是否可以並存。  
  
 下表顯示識別屬性。  
  
|屬性|用途|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|完整描述組件的識別。|  
|<xref:System.Reflection.AssemblyVersionAttribute>|指定組件的版本。|  
|<xref:System.Reflection.AssemblyCultureAttribute>|指定組件所支援的文化特性。|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|指定是否支援在相同電腦上、相同處理程序中或相同應用程式定義域中並存執行組件。|  
  
### <a name="informational-attributes"></a>資訊屬性  
 您可以使用資訊屬性，以提供組件其他的公司或產品資訊。 下表顯示 <xref:System.Reflection?displayProperty=nameWithType> 命名空間中定義的資訊屬性。  
  
|屬性|用途|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|定義自訂屬性，以指定組件資訊清單的產品名稱。|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|定義自訂屬性，以指定組件資訊清單的商標。|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|定義自訂屬性，以指定組件資訊清單的資訊版本。|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|定義自訂屬性，以指定組件資訊清單的公司名稱。|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|定義自訂屬性，以指定組件資訊清單的版權。|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|指示編譯器使用 Win32 檔案版本資源的特定版本號碼。|  
|<xref:System.CLSCompliantAttribute>|表示組件是否符合 Common Language Specification (CLS) 規範。|  
  
### <a name="assembly-manifest-attributes"></a>組件資訊清單屬性。  
 您可以使用組件資訊清單屬性，在組件資訊清單中提供資訊。 這包括標題、描述、預設別名和組態。 下表顯示 <xref:System.Reflection?displayProperty=nameWithType> 命名空間中定義的資訊清單屬性。  
  
|屬性|用途|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|定義自訂屬性，以指定組件資訊清單的組件標題。|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|定義自訂屬性，以指定組件資訊清單的組件描述。|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|定義自訂屬性，以指定組件資訊清單的組件設定 (例如零售或偵錯)。|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|定義組件資訊清單的易記預設別名。|  
  
##  <a name="Obsolete"></a> Obsolete 屬性  
 `Obsolete` 屬性會將程式實體標記為不再建議使用的標記。 每次使用標記為已淘汰的實體都會接著產生警告或錯誤 (視屬性的設定方式而定)。 例如:   
  
```vb  
<System.Obsolete("use class B")>   
Class A  
    Sub Method()  
    End Sub  
End Class  
  
Class B  
    <System.Obsolete("use NewMethod", True)>   
    Sub OldMethod()  
    End Sub  
  
    Sub NewMethod()  
    End Sub  
End Class  
```  
  
 在此範例中，`Obsolete` 屬性會套用至 `A` 類別和 `B.OldMethod` 方法。 因為套用至 `B.OldMethod` 的屬性建構函式的第二個引數設為 `true`，所以這個方法會造成編譯器錯誤，而使用 `A` 類別則只會產生警告。 不過，呼叫 `B.NewMethod` 不會產生任何警告或錯誤。  
  
 提供為屬性建構函式的第一個引數的字串將會顯示為警告或錯誤的一部分。 例如，當您將它與先前的定義搭配使用時，下列程式碼會產生兩個警告和一個錯誤︰  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 會產生 `A` 類別的兩個警告︰一個用於宣告類別參考，一個則用於類別建構函式。  
  
 可以使用沒有引數的 `Obsolete` 屬性，但包括項目為何已淘汰以及建議改使用之項目的說明。  
  
 `Obsolete` 屬性是單次使用屬性，並且可以套用至任何允許屬性的實體。 `Obsolete` 是 <xref:System.ObsoleteAttribute> 的別名。  
  
##  <a name="Conditional"></a> 條件式屬性  
 `Conditional` 屬性會根據前置處理識別碼來執行方法。 `Conditional` 屬性是 <xref:System.Diagnostics.ConditionalAttribute> 的別名，而且可以套用至方法或屬性類別。  
  
 在此範例中，`Conditional` 會套用至方法，以啟用或停用程式特定診斷資訊的顯示︰  
  
```vb  
#Const TRACE_ON = True  
Imports System  
Imports System.Diagnostics  
Module TestConditionalAttribute  
    Public Class Trace  
        <Conditional("TRACE_ON")>   
        Public Shared Sub Msg(ByVal msg As String)  
            Console.WriteLine(msg)  
        End Sub  
  
    End Class  
  
    Sub Main()  
        Trace.Msg("Now in Main...")  
        Console.WriteLine("Done.")  
    End Sub  
End Module  
```  
  
 如果未定義 `TRACE_ON` 識別碼，則不會顯示任何追蹤輸出。  
  
 `Conditional` 屬性通常與 `DEBUG` 識別碼搭配使用，以啟用偵錯組建 (而非版本組建) 的追蹤和記錄功能，與下面類似：  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 呼叫標記為條件的方法時，所指定前置處理符號的存在與否會決定包含還是省略呼叫。 如果定義符號，則會包括呼叫；否則會省略呼叫。 使用 `Conditional` 是 `#if…#endif` 區塊內封入方法的更乾淨、更明確且不容易出錯的替代方式，與下面類似：  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 條件式方法必須是類別或結構宣告中的方法，而且不能有傳回值。  
  
### <a name="using-multiple-identifiers"></a>使用多個識別碼  
 如果方法有多個 `Conditional` 屬性，則在定義至少一個條件式符號時會包括方法的呼叫 (換句話說，會使用 OR 運算子以邏輯方式將符號連結在一起)。 在此範例中，如果有 `A` 或 `B`，則會導致方法呼叫：  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 若要達到使用 AND 運算子以邏輯方式連結符號的效果，您可以定義序列條件式方法。 例如，只有在同時定義 `A` 和 `B` 時，才會執行下面的第二個方法：  
  
```vb  
<Conditional("A")>   
Shared Sub DoIfA()  
    DoIfAandB()  
End Sub  
  
<Conditional("B")>   
Shared Sub DoIfAandB()  
    ' Code to execute when both A and B are defined...  
End Sub  
```  
  
### <a name="using-conditional-with-attribute-classes"></a>搭配使用條件式與屬性類別  
 `Conditional` 屬性也可以套用至屬性類別定義。 在此範例中，如果定義 DEBUG，則自訂屬性 `Documentation` 只會將資訊新增至中繼資料。  
  
```vb  
<Conditional("DEBUG")>   
Public Class Documentation  
    Inherits System.Attribute  
    Private text As String  
    Sub New(ByVal doc_text As String)  
        text = doc_text  
    End Sub  
End Class  
  
Class SampleClass  
    ' This attribute will only be included if DEBUG is defined.  
    <Documentation("This method displays an integer.")>   
    Shared Sub DoWork(ByVal i As Integer)  
        System.Console.WriteLine(i)  
    End Sub  
End Class  
```  
  
##  <a name="CallerInfo"></a> 呼叫端資訊屬性  
 使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。 您可以取得原始程式碼的檔案路徑、原始程式碼中的行號，以及呼叫端的成員名稱。  
  
 若要取得成員呼叫端資訊，請使用套用至選擇性參數的屬性。 每個選擇性參數都會指定預設值。 下表列出 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間中定義的 Caller Info 屬性：  
  
|屬性|描述|類型|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|包含呼叫端的原始程式檔完整路徑。 這是編譯時期的路徑。|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|原始程式檔中呼叫方法的行號。|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|呼叫端的方法名稱或屬性名稱。 如需詳細資訊，請參閱[呼叫端資訊 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)。|`String`|  
  
 如需 Caller Info 屬性的詳細資訊，請參閱[呼叫端資訊 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)。  
  
##  <a name="VB"></a>Visual Basic 屬性  
 下表列出 Visual Basic 特有的屬性。  
  
|屬性|用途|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|表示編譯器應該為 COM 物件公開的類別。|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|允許存取使用只限定性條件該模組所需的模組成員。|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|使用結構中指定固定長度字串的大小，使用檔案輸入和輸出函式。|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|使用結構中指定固定陣列的大小，使用檔案輸入和輸出函式。|  
  
### <a name="comclassattribute"></a>COMClassAttribute  
 使用`COMClassAttribute`簡化從 Visual Basic 建立 COM 元件的程序。 COM 物件會從.NET Framework 組件，並沒有差異很大`COMClassAttribute`，您必須遵循一些步驟來產生 Visual basic 的 COM 物件。 針對類別標記為`COMClassAttribute`，編譯器會自動執行其中許多步驟。  
  
### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute  
 使用`HideModuleNameAttribute`以允許存取的使用只限定性條件該模組所需的模組成員。  
  
### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute  
 使用`VBFixedStringAttribute`強制 Visual Basic 來建立固定長度字串。 根據預設的可變長度的字串是，將字串儲存至檔案時，此屬性才有用。 下列程式碼示範：  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a>VBFixedArrayAttribute  
 使用`VBFixedArrayAttribute`來宣告陣列的大小固定的。 例如 Visual Basic 字串陣列是預設的可變長度。 這個屬性會序列化，或將資料寫入至檔案時很有用。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Visual Basic 程式設計手冊](../../../../visual-basic/programming-guide/index.md)  
 [屬性](../../../../../docs/standard/attributes/index.md)  
 [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [使用反映存取屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
