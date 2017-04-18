---
title: "Enhancing Debugging with the Debugger Display Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "debugger, display attributes"
  - "DebuggerTypeProxyAttribute attribute"
  - "debugging [.NET Framework], debugger display attributes"
  - "DebuggerDisplayAttribute attribute"
  - "display attributes for debugger"
  - "DebuggerBrowsableAttribute attribute"
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# Enhancing Debugging with the Debugger Display Attributes
偵錯工具顯示屬性可讓型別的開發人員 \(也就是指定該型別的執行階段行為，而同時也最了解這個行為的人\) 也能夠指定當該型別顯示在偵錯工具中時的面貌為何。  此外，提供 `Target` 屬性的偵錯工具顯示屬性可以由使用者在組件層級套用，而不需要了解原始程式碼。  <xref:System.Diagnostics.DebuggerDisplayAttribute> 屬性可控制型別或成員如何顯示在偵錯工具變數視窗中。  <xref:System.Diagnostics.DebuggerBrowsableAttribute> 屬性可決定欄位或屬性是否會顯示在偵錯工具變數視窗中，以及其顯示的方式。  <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 屬性可為型別指定替代型別或 Proxy，以及變更該型別顯示在偵錯工具視窗中的方式。  當您檢視有 Proxy 或替代型別的變數時，此 Proxy 表示偵錯工具顯示視窗中的原始型別。偵錯工具**變數視窗**只會顯示 proxy 型別的 Public 成員。  私用成員不會顯示。  
  
## 使用 DebuggerDisplayAttribute  
 <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> 建構函式有單一個引數：要顯示在型別執行個體之值欄中的字串，  這個字串包含括號 \({ 和 }\)。  一對括號中的文字會評估為運算式；  例如，下列 C\# 程式碼在選取加號 \(\+\) 來展開 `MyHashtable` 執行個體的偵錯工具顯示時，會顯示 "Count \= 4"。  
  
```  
[DebuggerDisplay("Count = {count}")]  
class MyHashtable  
{  
    public int count = 4;  
}  
```  
  
 套用到此運算式中參考之屬性 \(Property\) 的屬性 \(Attribute\) 不會予以處理。  對於 C\# 編譯器而言，允許使用一般運算式 \(此運算式對於目標型別的目前執行個體，只會有這個參考的隱含存取權\)。  此運算式有受到限制；無法存取別名、區域變數或指標。  在 C\# 程式碼中，您可以使用括號之間的一般運算式，此運算式只能對目標型別的目前執行個體之 `this` 指標有隱含存取權。  
  
 例如，如果 C\# 物件有被覆寫的 `ToString()`，偵錯工具將會呼叫此覆寫，並顯示其結果，而不是標準 `{<typeName>}.`；因此，如果有被覆寫的 `ToString()`，則不需要使用 <xref:System.Diagnostics.DebuggerDisplayAttribute>。  如果兩者都使用，<xref:System.Diagnostics.DebuggerDisplayAttribute> 屬性則會優先於 `ToString()` 覆寫。  
  
## 使用 DebuggerBrowsableAttribute  
 將 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 套用到欄位或屬性，以指定此欄位或屬性要如何顯示在偵錯工具視窗中。  此屬性的建構函式會接受其中一個 <xref:System.Diagnostics.DebuggerBrowsableState> 列舉值，這個值可指定下列其中一個狀態：  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState> 指出該成員不會顯示在資料視窗中。例如，在欄位上讓 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 使用這個值，會從階層架構移除該欄位，當您按一下型別執行個體的加號 \(\+\)，展開封入型別時，不會顯示該欄位。  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState> 指出會顯示該成員，但預設為不展開。這是預設行為。  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState> 表示不會顯示成員本身，但如果它是陣列或集合，則會顯示它的構成物件。  
  
> [!NOTE]
>  在 .NET Framework 2.0 版中，Visual Basic 不支援 <xref:System.Diagnostics.DebuggerBrowsableAttribute>。  
  
 下列程式碼範例將顯示 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 的用法，以防止其跟隨的屬性出現在類別的偵錯視窗中。  
  
```  
[DebuggerBrowsable(DebuggerBrowsableState.Never)]  
public static string y = "Test String";  
```  
  
## 使用 DebuggerTypeProxy  
 當您需要大規模地從根本變更某型別的偵錯檢視，但不要變更該型別本身時，請使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 屬性。  <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 屬性是用來指定型別的顯示 Proxy，讓開發人員可以修改此型別的檢視。這個屬性就像 <xref:System.Diagnostics.DebuggerDisplayAttribute> 一樣，可以在組件層級使用，此時 <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> 屬性會指定 Proxy 將使用的型別。  建議的用法是讓這個屬性指定此型別內發生的私用巢狀型別 \(這個屬性將會套用到此型別\)。型別顯示時，支援型別檢視器的運算式評估工具會檢查這個屬性 \(Attribute\)。  如果找到這個屬性 \(Attribute\)，運算式評估工具會為套用這個屬性 \(Attribute\) 的型別取代顯示 Proxy 型別。  
  
 如果有 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 時，偵錯工具變數視窗只會顯示 Proxy 型別的公用成員。  私用成員不會顯示。  有屬性增強的檢視不會變更資料視窗的行為。  
  
 為了避免不必要的效能負面影響，顯示 Proxy 的屬性要等到展開物件之後，才會予以處理，其處理方式是由使用者按一下資料視窗內型別旁邊的加號 \(\+\)，或是套用 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 屬性。  因此，建議您不要將屬性套用至顯示型別上。  屬性可以且應該套用到顯示型別的主體中。  
  
 下列程式碼範例將示範 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 的用法，以指定要當做偵錯工具顯示 Proxy 使用的型別。  
  
```  
  
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
  
## 範例  
  
### 說明  
 下列程式碼範例可以在 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 中檢視，以查看套用 <xref:System.Diagnostics.DebuggerDisplayAttribute>、<xref:System.Diagnostics.DebuggerBrowsableAttribute> 和 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 屬性的結果。  
  
### 程式碼  
 [!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
 [!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
 [!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]  
  
## 請參閱  
 <xref:System.Diagnostics.DebuggerDisplayAttribute>   
 <xref:System.Diagnostics.DebuggerBrowsableAttribute>   
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>