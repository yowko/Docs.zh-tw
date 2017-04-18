---
title: "常見屬性 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f470e6ff3e316076d71a34346f741cc4504471a3
ms.lasthandoff: 03/13/2017

---
# <a name="common-attributes-visual-basic"></a>常見屬性 (Visual Basic)
本主題說明 Visual Basic 程式中最常用的屬性。  
  
-   [全域屬性](#Global)  
  
-   [過時的屬性](#Obsolete)  
  
-   [條件式屬性](#Conditional)  
  
-   [呼叫端資訊屬性](#CallerInfo)  
  
-   [Visual Basic 屬性](#VB)  
  
##  <a name="Global"></a>全域屬性  
 大部分的屬性會套用至特定語言項目，例如類別或方法。不過，有些屬性是全域 — 它們適用於整個組件或模組。 例如，<xref:System.Reflection.AssemblyVersionAttribute>屬性可以用來內嵌為組件，就像這樣的版本資訊︰</xref:System.Reflection.AssemblyVersionAttribute>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 之後，任何全域屬性會出現在原始碼最上層`Imports`陳述式之前的任何型別、 模組或命名空間宣告。 全域屬性可以出現在多個原始程式檔，但必須在單一編譯階段編譯檔案。 Visual Basic 專案中，全域屬性通常會放在 AssemblyInfo.vb 檔案 （檔案時自動建立 Visual Studio 中建立專案）。  
  
 組件屬性是提供組件相關資訊的值。 它們可分成下列類別︰  
  
-   組件的識別屬性  
  
-   資訊屬性  
  
-   組件資訊清單屬性  
  
### <a name="assembly-identity-attributes"></a>組件識別屬性  
 （以強式名稱，如果適用的話） 的三個屬性會決定組件的識別︰ 名稱、 版本和文化特性。 這些屬性會形成組件的完整名稱，並在程式碼中參考它時所需。 您可以設定組件的版本和文化特性使用的屬性。 不過，編譯器，Visual Studio IDE 中設定的名稱值[組件資訊對話方塊](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box)，或組件連結器 (Al.exe) 建立組件時，根據包含組件資訊清單的檔案。 <xref:System.Reflection.AssemblyFlagsAttribute>屬性會指定是否可以並存組件的多個副本。</xref:System.Reflection.AssemblyFlagsAttribute>  
  
 下表顯示識別屬性。  
  
|屬性|用途|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName>|完整描述組件的識別。|  
|<xref:System.Reflection.AssemblyVersionAttribute></xref:System.Reflection.AssemblyVersionAttribute>|指定組件的版本。|  
|<xref:System.Reflection.AssemblyCultureAttribute></xref:System.Reflection.AssemblyCultureAttribute>|指定組件所支援的文化特性。|  
|<xref:System.Reflection.AssemblyFlagsAttribute></xref:System.Reflection.AssemblyFlagsAttribute>|指定組件是否支援在同一部電腦，在相同的程序，或在相同的應用程式定義域中的並存執行。|  
  
### <a name="informational-attributes"></a>資訊屬性  
 您可以使用資訊屬性，以提供組件其他的公司或產品資訊。 下表顯示資訊的屬性中定義<xref:System.Reflection?displayProperty=fullName>命名空間。</xref:System.Reflection?displayProperty=fullName>  
  
|屬性|用途|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute></xref:System.Reflection.AssemblyProductAttribute>|定義自訂屬性來指定組件資訊清單的產品名稱。|  
|<xref:System.Reflection.AssemblyTrademarkAttribute></xref:System.Reflection.AssemblyTrademarkAttribute>|定義自訂屬性來指定組件資訊清單的商標。|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute></xref:System.Reflection.AssemblyInformationalVersionAttribute>|定義自訂屬性來指定組件資訊清單的資訊版本。|  
|<xref:System.Reflection.AssemblyCompanyAttribute></xref:System.Reflection.AssemblyCompanyAttribute>|定義自訂屬性來指定組件資訊清單的公司名稱。|  
|<xref:System.Reflection.AssemblyCopyrightAttribute></xref:System.Reflection.AssemblyCopyrightAttribute>|定義自訂屬性來指定組件資訊清單的著作權。|  
|<xref:System.Reflection.AssemblyFileVersionAttribute></xref:System.Reflection.AssemblyFileVersionAttribute>|會指示編譯器使用 Win32 檔案版本資源的特定版本號碼。|  
|<xref:System.CLSCompliantAttribute></xref:System.CLSCompliantAttribute>|表示組件是否使用 Common Language Specification (CLS) 相容。|  
  
### <a name="assembly-manifest-attributes"></a>組件資訊清單屬性。  
 您可以使用組件資訊清單屬性在組件資訊清單中提供資訊。 這包括標題、 描述、 預設別名和組態。 下表顯示組件資訊清單屬性定義於<xref:System.Reflection?displayProperty=fullName>命名空間。</xref:System.Reflection?displayProperty=fullName>  
  
|屬性|用途|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute></xref:System.Reflection.AssemblyTitleAttribute>|定義自訂屬性來指定組件資訊清單的組件標題。|  
|<xref:System.Reflection.AssemblyDescriptionAttribute></xref:System.Reflection.AssemblyDescriptionAttribute>|定義自訂屬性來指定組件資訊清單的組件描述。|  
|<xref:System.Reflection.AssemblyConfigurationAttribute></xref:System.Reflection.AssemblyConfigurationAttribute>|定義自訂屬性來指定 （例如正式版本或偵錯） 的組件組態的組件資訊清單。|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute></xref:System.Reflection.AssemblyDefaultAliasAttribute>|定義組件資訊清單的好記的預設別名|  
  
##  <a name="Obsolete"></a>過時的屬性  
 `Obsolete`屬性標記為不再建議使用的程式實體。 每次使用的實體標記為過時接著會產生警告或錯誤，視屬性的設定方式而定。 例如:   
  
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
  
 在此範例中`Obsolete`屬性套用至類別`A`和方法`B.OldMethod`。 因為屬性建構函式的第二個引數套用至`B.OldMethod`設為`true`，這個方法會造成編譯器錯誤，而使用類別`A`將只是產生警告。 呼叫`B.NewMethod`，不過，會產生任何警告或錯誤。  
  
 提供為屬性建構函式的第一個引數的字串將顯示為警告或錯誤的一部分。 例如，當您使用先前的定義，下列程式碼會產生兩個警告和一個錯誤︰  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 類別的兩個警告`A`產生︰ 一個用於類別參考宣告，一個類別建構函式。  
  
 `Obsolete`屬性可以用不含引數，但說明的原因包括項目已經過時，建議改用。  
  
 `Obsolete`屬性的單一用途的屬性，並可套用至任何允許屬性的實體。 `Obsolete`<xref:System.ObsoleteAttribute>.</xref:System.ObsoleteAttribute>的別名  
  
##  <a name="Conditional"></a>條件式屬性  
 `Conditional`屬性，讓方法的執行取決於前置處理識別項。 `Conditional`屬性為其別名<xref:System.Diagnostics.ConditionalAttribute>，而且可以套用至方法或屬性類別</xref:System.Diagnostics.ConditionalAttribute>  
  
 在此範例中，`Conditional`套用至方法，以啟用或停用程式特定的診斷資訊的顯示︰  
  
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
  
 如果`TRACE_ON`識別碼未定義時，將會顯示任何追蹤輸出。  
  
 `Conditional`屬性通常用於`DEBUG`識別碼可啟用追蹤和記錄功能偵錯組建，但是不能在發行組建，如下所示︰  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 呼叫方法，標示為條件時，所指定的前置處理符號存在會決定包含或省略呼叫。 如果定義的符號時，呼叫就是包含在內。否則，呼叫會省略。 使用`Conditional`是更乾淨更優雅且較不容易出錯的替代方案封入方法內`#if…#endif`區塊，就像這樣︰  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 條件式方法必須是類別或結構的宣告中的方法，並不能傳回的值。  
  
### <a name="using-multiple-identifiers"></a>使用多個識別項  
 如果方法具有多個`Conditional`屬性、 方法的呼叫會包括至少一個條件式的符號定義 （亦即，符號會以邏輯方式連結在一起使用 OR 運算子）。 在此範例中的其中一個存在`A`或`B`方法呼叫會導致︰  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 若要達到以邏輯方式將符號連結使用 AND 運算子的效果，您可以定義序列的條件式方法。 例如，下列第二個方法才會執行這兩個`A`和`B`所定義︰  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>使用條件式屬性類別  
 `Conditional`屬性也可以套用至屬性的類別定義。 在此範例中，自訂屬性`Documentation`只將資訊加入中繼資料如果定義偵錯。  
  
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
  
##  <a name="CallerInfo"></a>呼叫端資訊屬性  
 使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。 您可以取得原始程式碼的檔案路徑、 原始程式碼和呼叫端的成員名稱中的行號。  
  
 若要取得成員呼叫端資訊，您可以使用套用至選擇性參數的屬性。 每個選擇性參數指定預設值。 下表列出中所定義的 Caller Info 屬性<xref:System.Runtime.CompilerServices?displayProperty=fullName>命名空間︰</xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
|屬性|描述|類型|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute></xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|包含呼叫端的原始程式檔完整路徑。 這是在編譯時期的路徑。|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|呼叫此方法的原始程式檔中的行號。|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|方法名稱或呼叫端的屬性名稱。 如需詳細資訊，請參閱[呼叫端資訊 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)。|`String`|  
  
 如需 Caller Info 屬性的詳細資訊，請參閱[呼叫端資訊 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)。  
  
##  <a name="VB"></a>Visual Basic 屬性  
 下表列出可針對 Visual Basic 的屬性。  
  
|屬性|用途|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute>|指示編譯器應該為 COM 物件公開的類別。|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute></xref:Microsoft.VisualBasic.HideModuleNameAttribute>|可讓您使用只限定性條件所需的模組存取模組成員。|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute></xref:Microsoft.VisualBasic.VBFixedStringAttribute>|使用結構中指定的固定長度字串大小，檔案輸入和輸出函式。|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute></xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|使用結構中指定固定陣列的大小，檔案輸入和輸出函式。|  
  
### <a name="comclassattribute"></a>COMClassAttribute  
 使用`COMClassAttribute`來簡化從 Visual Basic 建立 COM 元件的程序。 COM 物件會從.NET Framework 組件，而大幅不同`COMClassAttribute`，您必須遵循幾個步驟來產生 Visual basic 的 COM 物件。 對於類別標記與`COMClassAttribute`，編譯器會自動執行許多這些步驟。  
  
### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute  
 使用`HideModuleNameAttribute`以允許存取的使用只限定性條件模組所需的模組成員。  
  
### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute  
 使用`VBFixedStringAttribute`強制 Visual Basic 來建立固定長度字串。 字串具有可變長度，根據預設，並將字串儲存至檔案時，這個屬性很有用。 下列程式碼示範︰  
  
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
 使用`VBFixedArrayAttribute`來宣告為固定大小的陣列。 像 Visual Basic 字串陣列是預設的可變長度。 這個屬性會序列化，或將資料寫入至檔案時很有用。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection></xref:System.Reflection>   
 <xref:System.Attribute></xref:System.Attribute>   
 [Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md)   
 [屬性](https://msdn.microsoft.com/library/5x6cd29c)   
 [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [使用反映 (Visual Basic) 存取屬性](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
