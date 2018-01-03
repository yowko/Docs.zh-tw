---
title: "使用偵錯工具顯示屬性增強偵錯功能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac5097326ae76a8790569c13fd8b1285b0cfeec0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>使用偵錯工具顯示屬性增強偵錯功能
偵錯工具顯示屬性能讓指定並最了解該類型執行階段行為的開發人員，也指定該類型在偵錯工具中顯示的外觀。 此外，提供 `Target` 屬性的偵錯工具顯示屬性，也可供沒有原始程式碼背景的使用者在組件層級使用。 <xref:System.Diagnostics.DebuggerDisplayAttribute> 屬性控制類型或成員在偵錯工具變數視窗中顯示的方式。 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 屬性決定欄位或屬性是否以及如何顯示在偵錯工具變數視窗中。 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 屬性會指定類型的替代類型 (或 Proxy)，並且變更在偵錯工具視窗中顯示類型的方式。 當您檢視有 Proxy (或替代類型) 的變數時，Proxy 會替代偵錯工具顯示視窗中的原始類型**。** 偵錯工具變數視窗只會顯示 Proxy 類型的 Public 成員。 私用成員不會顯示。  
  
## <a name="using-the-debuggerdisplayattribute"></a>使用 DebuggerDisplayAttribute  
 <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> 建構函式有單一引數：在類型執行個體的 [值] 一欄中顯示的字串。 這個字串可以包含括弧 ({ 和 })。 括弧內的文字會評估為運算式。 例如，下列 C# 程式碼會在選取加號 (+) 時顯示 "Count = 4"，展開偵錯工具顯示的 `MyHashtable` 執行個體。  
  
```csharp
[DebuggerDisplay("Count = {count}")]  
class MyHashtable  
{  
    public int count = 4;  
}  
```
  
 不處理套用至運算式參考屬性 (property) 的屬性 (attribute)。 在 C# 編譯器，一般運算式僅能以隱含方式存取目標類型目前執行個體的此一參考。 運算式有限制，不能存取別名、區域變數或指標。 在 C# 程式碼中，您可以使用以括弧括住的一般運算式，以隱含方式存取目標類型目前執行個體的 `this` 指標。  
  
 例如，如果 C# 物件具有覆寫的 `ToString()`，則偵錯工具會呼叫覆寫並顯示它的結果，而不是標準的 `{<typeName>}.`。因此，如果您已覆寫 `ToString()`，就不需要使用 <xref:System.Diagnostics.DebuggerDisplayAttribute>。 如果兩者都使用，<xref:System.Diagnostics.DebuggerDisplayAttribute> 屬性則會優先於 `ToString()` 覆寫。  
  
## <a name="using-the-debuggerbrowsableattribute"></a>使用 DebuggerBrowsableAttribute  
 將 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 套用至欄位或屬性，以指定欄位或屬性在偵錯工具視窗中的顯示方式。 這個屬性的建構函式會使用其中一個 <xref:System.Diagnostics.DebuggerBrowsableState> 列舉值，指定下列狀態之一：  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState.Never> 指出成員未顯示在資料視窗中。  例如，對欄位的 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 使用此值，會從階層中移除欄位；當您按一下類型執行個體的加號 (+) 展開封入類型時，不會顯示欄位。  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> 指出已顯示成員，但預設不展開。  這是預設行為。  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> 指出成員本身不會顯示，但如果它是陣列或集合，則會顯示其組成物件。  
  
> [!NOTE]
>  .NET Framework 2.0 版中的 Visual Basic 不支援 <xref:System.Diagnostics.DebuggerBrowsableAttribute>。  
  
 下列程式碼範例示範，使用 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 防止它後面的屬性出現在類別的偵錯視窗中。  
  
```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]  
public static string y = "Test String";  
```  
  
## <a name="using-the-debuggertypeproxy"></a>使用 DebuggerTypeProxy  
 當您需要大幅並從本質上變更類型的偵錯檢視，但不是變更類型本身時，請使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 屬性。 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 屬性用來指定類型的顯示 Proxy，讓開發人員調整類型的檢視。  這個屬性，如 <xref:System.Diagnostics.DebuggerDisplayAttribute>，可以用在組件層級；如此 <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> 屬性會指定要使用 Proxy 的類型。 建議的用法是，這個屬性指定的私用巢狀類型，會出現在要套用屬性的類型內。  顯示類型時，支援類型檢視器的運算式評估工具會檢查這個屬性。 如果找到屬性，運算式評估工具會用顯示 Proxy 類型替代套用屬性的類型。  
  
 當 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 出現時，偵錯工具變數視窗只會顯示 Proxy 類型的 Public 成員。 私用成員不會顯示。 屬性增強的檢視不會變更資料視窗的行為。  
  
 為避免不必要的效能損失，在使用者按一下資料視窗中類型旁的加號 (+)，或者套用 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 屬性展開物件之前，不會處理顯示 Proxy 的屬性。 因此，顯示類型不建議套用任何屬性。 屬性可以而且應該套用在顯示類型的主體中。  
  
 下列程式碼範例示範使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 指定類型，用為偵錯工具的顯示 Proxy。  
  
```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]  
class MyHashtable : Hashtable  
{  
    private const string TestString =   
        "This should not appear in the debug window.";  
  
    internal class HashtableDebugView  
    {  
        private Hashtable hashtable;  
        public const string TestStringProxy =   
            "This should appear in the debug window.";  
  
        // The constructor for the type proxy class must have a   
        // constructor that takes the target type as a parameter.  
        public HashtableDebugView(Hashtable hashtable)  
        {  
            this.hashtable = hashtable;  
        }  
    }  
}  
```  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 您可以在 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 中檢視下列程式碼範例，查看套用 <xref:System.Diagnostics.DebuggerDisplayAttribute>、<xref:System.Diagnostics.DebuggerBrowsableAttribute> 和 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 屬性的結果。  
  
### <a name="code"></a>程式碼  
 [!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
 [!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
 [!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Diagnostics.DebuggerDisplayAttribute>  
 <xref:System.Diagnostics.DebuggerBrowsableAttribute>  
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
