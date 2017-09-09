---
title: "指定完整的類型名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "組件 [.NET Framework], 名稱"
  - "巴克斯格式"
  - "BNF"
  - "完整類型名稱"
  - "IDENTIFIER"
  - "語言, BNF 文法"
  - "名稱 [.NET Framework], 組件"
  - "名稱 [.NET Framework], 完整類型名稱"
  - "反映, 完整類型名稱"
  - "特殊字元"
  - "語彙基元"
  - "類型名稱"
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 指定完整的類型名稱
您必須指定型別名稱，以使各種反映作業的輸入有效。  完整型別名稱由組件名稱規格、命名空間規格和型別名稱所構成。  型別名稱規格用於 <xref:System.Type.GetType%2A?displayProperty=fullName>、<xref:System.Reflection.Module.GetType%2A?displayProperty=fullName>、<xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=fullName> 和 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName> 等方法。  
  
## 型別名稱的 Backus\-Naur 格式文法  
 Backus\-Naur 格式 \(BNF\) 定義型式語言的語法。  以下表格列出 BNF 語彙規則，說明如何辨認有效輸入。  終端項 \(那些不能再進一步簡化的項目\) 全部以大寫字母顯示。  非終端項 \(那些可繼續簡化的項目\) 以大小寫混合或單引號括住的字串來表示，但單引號 \('\) 不是語法本身的一部分。  管道字元 \(&#124;\) 代表具有子規則的規則。  
  
|完整型別名稱的 BNF 文法|  
|--------------------|  
|TypeSpec                          :\=   ReferenceTypeSpec<br /><br /> &#124;     SimpleTypeSpec|  
|ReferenceTypeSpec            :\=   SimpleTypeSpec '&'|  
|SimpleTypeSpec                :\=   PointerTypeSpec<br /><br /> &#124;     ArrayTypeSpec<br /><br /> &#124;     TypeName|  
|PointerTypeSpec                :\=   SimpleTypeSpec '\*'|  
|ArrayTypeSpec                  :\=   SimpleTypeSpec '\[ReflectionDimension\]'<br /><br /> &#124;     SimpleTypeSpec '\[ReflectionEmitDimension\]'|  
|ReflectionDimension           :\=   '\*'<br /><br /> &#124;     ReflectionDimension ',' ReflectionDimension<br /><br /> &#124;     NOTOKEN|  
|ReflectionEmitDimension    :\=   '\*'<br /><br /> &#124;     Number '..'數字<br /><br /> &#124;     Number '…'<br /><br /> &#124;     ReflectionDimension ',' ReflectionDimension<br /><br /> &#124;     NOTOKEN|  
|Number                            :\=   \[0\-9\]\+|  
|TypeName                         :\=   NamespaceTypeName<br /><br /> &#124;     NamespaceTypeName ',' AssemblyNameSpec|  
|NamespaceTypeName        :\=   NestedTypeName<br /><br /> &#124;     NamespaceSpec '.'NestedTypeName|  
|NestedTypeName               :\=   IDENTIFIER<br /><br /> &#124;     NestedTypeName '\+' IDENTIFIER|  
|NamespaceSpec                 :\=   IDENTIFIER<br /><br /> &#124;     NamespaceSpec '.'IDENTIFIER|  
|AssemblyNameSpec           :\=   IDENTIFIER<br /><br /> &#124;     IDENTIFIER ',' AssemblyProperties|  
|AssemblyProperties            :\=   AssemblyProperty<br /><br /> &#124;     AssemblyProperties ',' AssemblyProperty|  
|AssemblyProperty              :\=   AssemblyPropertyName '\=' AssemblyPropertyValue|  
  
## 指定特殊字元  
 在型別名稱中，IDENTIFIER 為語言規則決定的任何有效名稱。  
  
 使用反斜線 \(\\\) 做為逸出字元 \(Escape Character\)，在當做 IDENTIFIER 一部分使用時，分隔下列語彙基元 \(Token\)。  
  
|語彙基元|意義|  
|----------|--------|  
|\\,|組件分隔符號。|  
|\\\+|巢狀型別分隔符號。|  
|\\&|參考型別。|  
|\\\*|指標型別。|  
|\\\[|陣列維度分隔符號。|  
|\\\]|陣列維度分隔符號。|  
|\\.|在句號之前使用反斜線，只限句號用於陣列規格內時。  NamespaceSpec 中的句號不接受反斜線。|  
|\\\\|反斜線，當需要當做字串常值 \(String Literal\) 時。|  
  
 注意，在所有 TypeSpec 元件中，除了 AssemblyNameSpec 以外，空格是有意義的。  在 AssemblyNameSpec 中，',' 分隔符號之前的空格有意義，但 ',' 分隔符號之後的空格則被忽略。  
  
 Reflection 類別 \(例如 <xref:System.Type.FullName%2A?displayProperty=fullName>\) 會傳回 mangled 名稱，使得該傳回名稱可用於對 <xref:System.Type.GetType%2A> 的呼叫，如同在 `MyType.GetType(myType.FullName)` 中一樣。  
  
 例如，型別的完整名稱可能為 `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`。  
  
 如果命名空間為 `Ozzy.Out+Back`，那麼反斜線必須置於加號之前。  否則，剖析器 \(Parser\) 將會解譯它為巢狀分隔符號。  反映發出這個字串為 `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`。  
  
## 指定組件名稱  
 組件名稱規格中所需最低限度的資訊為組件的文字名稱 \(IDENTIFIER\)。  您可以緊隨 IDENTIFIER 之後加入屬性\/值配組的逗號分隔清單，如下表的說明。  IDENTIFIER 命名應該遵循檔案命名規則。  IDENTIFIER 不區分大小寫。  
  
|屬性名稱|說明|允許值|  
|----------|--------|---------|  
|**Version**|組件版本號碼|*Major.Minor.Build.Revision*，其中 *Major*、*Minor*、*Build* 和 *Revision* 為 0 至包含 65535 之間的整數。|  
|**PublicKey**|完整公開金鑰|十六進位格式的完整公開金鑰字串值。  指定 null 參考 \(在 Visual Basic 中為 **Nothing**\)，以明確指示私用組件。|  
|**PublicKeyToken**|公開金鑰語彙基元 \(完整公開金鑰的 8 位元組雜湊\)|十六進位格式的公開金鑰語彙基元字串值。  指定 null 參考 \(在 Visual Basic 中為 **Nothing**\)，以明確指示私用組件。|  
|**文化特性**|組件文化特性|RFC\-1766 格式的組件文化特性，或與語言無關 \(非附屬\) 組件的「中性」。|  
|**Custom**|自訂二進位大型物件 \(BLOB\)。  這目前只用於[原生映像產生器 \(Ngen\)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 所產生的組件中。|原生映像產生器工具所使用的自訂字串，用來告知組件快取正在安裝的組件是原生映像，因此，要安裝在原生映像快取中。  也稱為 Zap 字串。|  
  
 下列範例說明含有預設文化特性的簡單命名組件之 **AssemblyName**。  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 下列程式碼範例說明強式名稱組件的完整指定參考，此組件具有文化特性 "en"。  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 下列各個程式碼範例說明部分指定的 **AssemblyName**，由強式或簡單命名組件都可滿足。  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 下列各個程式碼範例說明部分指定的 **AssemblyName**，必須由簡單命名組件滿足。  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 下列各個程式碼範例說明部分指定的 **AssemblyName**，必須由強式名稱組件滿足。  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## 指定指標  
 SimpleTypeSpec\* 代表 Unmanaged 指標。  例如，若要取得型別 MyType 的指標，請使用 `Type.GetType("MyType*")`。  若要取得型別 MyType 的指標，請使用 `Type.GetType("MyType**")`。  
  
## 指定參考  
 SimpleTypeSpec & 代表 Managed 指標或參考。  例如，若要取得型別 MyType 的參考，請使用 `Type.GetType("MyType &")`。  請注意，與指標不同的是，參考會被限制於一個層級。  
  
## 指定陣列  
 在 BNF 文法中，ReflectionEmitDimension 只套用於使用 <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=fullName> 所擷取的不完全型別定義。  不完全型別定義是指使用 [Reflection.Emit](frlrfSystemReflectionEmit) 但尚未呼叫 <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=fullName> 所建構的<xref:System.Reflection.Emit.TypeBuilder> 物件。  ReflectionDimension 可被用來擷取任何已完成的型別定義，也就是已載入的型別。  
  
 指定陣列陣序，以在反映中存取陣列：  
  
-   `Type.GetType("MyArray[]")` 取得以 0 為下限的一維陣列。  
  
-   `Type.GetType("MyArray[*]")` 取得未知下限的一維陣列。  
  
-   `Type.GetType("MyArray[][]")` 取得二維陣列的陣列。  
  
-   `Type.GetType("MyArray[*,*]")` 和 `Type.GetType("MyArray[,]")` 取得未知下限的矩形二維陣列。  
  
 請注意，從執行階段的觀點 \(`MyArray[] != MyArray[*]`\) 但是對於多維陣列來說，這兩個標記法是相等的。  也就是說，`Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` 會評估為 **true**。  
  
 對於 **ModuleBuilder.GetType** 而言，`MyArray[0..5]` 指示一維陣列，其大小為 6，下限為 0； `MyArray[4…]` 指示一維陣列，其大小未知，而下限為 4。  
  
## 請參閱  
 <xref:System.Reflection.AssemblyName>   
 <xref:System.Reflection.Emit.ModuleBuilder>   
 <xref:System.Reflection.Emit.TypeBuilder>   
 <xref:System.Type.FullName%2A?displayProperty=fullName>   
 <xref:System.Type.GetType%2A?displayProperty=fullName>   
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName>   
 [檢視類型資訊](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)