---
title: "指定完整的類型名稱 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- Backus-Naur form
- languages, BNF grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e1bceed0f95170f9dc11ebc28217b9e8a7dc891c
ms.contentlocale: zh-tw
ms.lasthandoff: 06/02/2017

---
<a id="specifying-fully-qualified-type-names" class="xliff"></a>

# 指定完整的類型名稱
您必須指定具有各種反映作業有效輸入的類型名稱。 完整的類型名稱包括組件名稱規格、命名空間規格和類型名稱。 方法使用的類型名稱規格如 <xref:System.Type.GetType%2A?displayProperty=fullName>、<xref:System.Reflection.Module.GetType%2A?displayProperty=fullName>、<xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=fullName> 和 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName>。  
  
<a id="backus-naur-form-grammar-for-type-names" class="xliff"></a>

## 類型名稱的巴克斯格式文法  
 巴克斯格式 (BNF) 會定義形式語言的語法。 下表列出 BNF 語彙規則，說明如何辨識有效的輸入。 終端項 (不會進一步縮減的那些項目) 全部以大寫字母顯示。 非終端項 (會進一步縮減的那些項目) 會以大小寫混合或單引號括住的字串顯示，但單引號 (') 不是語法本身的一部分。 縱線字元 (&#124;) 表示具有子規則的規則。  
  
|完整類型名稱的 BNF 文法|  
|-----------------------------------------------|  
|TypeSpec                          :=   ReferenceTypeSpec<br /><br /> &#124;     SimpleTypeSpec|  
|ReferenceTypeSpec            :=   SimpleTypeSpec '&'|  
|SimpleTypeSpec                :=   PointerTypeSpec<br /><br /> &#124;     ArrayTypeSpec<br /><br /> &#124;     TypeName|  
|PointerTypeSpec                :=   SimpleTypeSpec '*'|  
|ArrayTypeSpec                  :=   SimpleTypeSpec '[ReflectionDimension]'<br /><br /> &#124;     SimpleTypeSpec '[ReflectionEmitDimension]'|  
|ReflectionDimension           :=   '*'<br /><br /> &#124;     ReflectionDimension ',' ReflectionDimension<br /><br /> &#124;     NOTOKEN|  
|ReflectionEmitDimension    :=   '*'<br /><br /> &#124;     Number '..' 數字<br /><br /> &#124;     Number '…'<br /><br /> &#124;     ReflectionDimension ',' ReflectionDimension<br /><br /> &#124;     NOTOKEN|  
|Number                            :=   [0-9]+|  
|TypeName                         :=   NamespaceTypeName<br /><br /> &#124;     NamespaceTypeName ',' AssemblyNameSpec|  
|NamespaceTypeName        :=   NestedTypeName<br /><br /> &#124;     NamespaceSpec '.'NestedTypeName|  
|NestedTypeName               :=   IDENTIFIER<br /><br /> &#124;     NestedTypeName '+' IDENTIFIER|  
|NamespaceSpec                 :=   IDENTIFIER<br /><br /> &#124;     NamespaceSpec '.'IDENTIFIER|  
|AssemblyNameSpec           :=   IDENTIFIER<br /><br /> &#124;     IDENTIFIER ',' AssemblyProperties|  
|AssemblyProperties            :=   AssemblyProperty<br /><br /> &#124;     AssemblyProperties ',' AssemblyProperty|  
|AssemblyProperty              :=   AssemblyPropertyName '=' AssemblyPropertyValue|  
  
<a id="specifying-special-characters" class="xliff"></a>

## 指定特殊字元  
 類型名稱中的 IDENTIFIER 是語言規則判定的任何有效名稱。  
  
 將反斜線 (\\) 用作逸出字元，分隔下列作為 IDENTIFIER 一部分的權杖。  
  
|語彙基元|意義|  
|-----------|-------------|  
|\\,|組件分隔符號。|  
|\\+|巢狀型別分隔符號。|  
|\\&|參考型別。|  
|\\*|指標類型。|  
|\\[|陣列維度分隔符號。|  
|\\]|陣列維度分隔符號。|  
|\\.|句號只有用在陣列規格中時，前面才會使用反斜線。 NamespaceSpec 中的句號不接受反斜線。|  
|\\\|反斜線會視需要當成字串常值。|  
  
 請注意，除 AssemblyNameSpec 以外的所有 TypeSpec 元件中，空格都是相關的。 在 AssemblyNameSpec 中，',' 分隔符號之前的空格是相關的，但 ',' 分隔符號之後的空格則會忽略。  
  
 <xref:System.Type.FullName%2A?displayProperty=fullName> 之類的反映類別會傳回損害的名稱，所以傳回的名稱可用於呼叫 <xref:System.Type.GetType%2A>，如在 `MyType.GetType(myType.FullName)` 中一樣。  
  
 例如，類型的完整名稱可能是 `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`。  
  
 如果以前的命名空間是 `Ozzy.Out+Back`，則反斜線前面必須有加號。 否則，剖析器會將它解譯為巢狀分隔符號。 反映將此字串發出為 `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`。  
  
<a id="specifying-assembly-names" class="xliff"></a>

## 指定組件名稱  
 組件名稱規格中的基本資訊是組件的文字名稱 (IDENTIFIER)。 您可以按照逗號分隔的屬性/值組清單理解 IDENTIFIER，如下表所述。 IDENTIFIER 的命名應依照檔案命名的規則。 IDENTIFIER 不區分大小寫。  
  
|屬性名稱|描述|允許的值|  
|-------------------|-----------------|----------------------|  
|**版本**|組件版本號碼|在 *Major.Minor.Build.Revision* 中，*Major*、*Minor*、*Build* 和 *Revision* 是介於 0 到 65535 (含) 之間的整數。|  
|**PublicKey**|完整公開金鑰|十六進位格式的完整公開金鑰字串值。 指定 null 參考 (Visual Basic 為**Nothing**) 以明確指出私用組件。|  
|**PublicKeyToken**|公開金鑰語彙基元 (完整公開金鑰的 8 位元組雜湊)|十六進位格式的公開金鑰語彙基元字串值。 指定 null 參考 (Visual Basic 為 **Nothing**) 以明確指出私用組件。|  
|**文化特性**|組件文化特性|RFC-1766 格式的組件文化特性，或「中性的」語言無關 (非附屬) 組件。|  
|**自訂**|自訂二進位大型物件 (BLOB)。 目前只用於[原生映像產生器 (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 產生的組件。|自訂原生映像產生器工具所用的字串用於通知組件快取安裝中的組件是原生映像，因此要安裝在原生映像快取中。 也稱為 zap 字串。|  
  
 下例示範的 **AssemblyName**，僅以預設文化特性命名組件。  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 下例顯示具有 "en" 文化特性之強式名稱組件的完整指定參考。  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 下列範例各自都有部分指定的 **AssemblyName**，無論強式或簡單名稱組件皆可滿足。  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 下列範例各自都有部分指定的 **AssemblyName**，必須由簡單名稱組件滿足。  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 下列範例各自都有部分指定的 **AssemblyName**，必須由強式名稱組件滿足。  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
<a id="specifying-pointers" class="xliff"></a>

## 指定指標  
 SimpleTypeSpec* 表示 Unmanaged 指標。 例如，若要取得類型 MyType 的指標，請使用 `Type.GetType("MyType*")`。 若要取得類型 MyType 指標的指標，請使用 `Type.GetType("MyType**")`。  
  
<a id="specifying-references" class="xliff"></a>

## 指定參考  
 SimpleTypeSpec & 代表 Managed 指標或參考。 例如，若要取得類型 MyType 的參考，請使用 `Type.GetType("MyType &")`。 請注意，參考與指標不同，僅限一個層級。  
  
<a id="specifying-arrays" class="xliff"></a>

## 指定陣列  
 在 BNF 文法中，ReflectionEmitDimension 只適用於使用 <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=fullName> 擷取的不完整類型定義。 不完整的類型定義是使用 <xref:System.Reflection.Emit?displayProperty=fullName> 建構卻未呼叫 <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=fullName> 的 <xref:System.Reflection.Emit.TypeBuilder> 物件。 ReflectionDimension 可以用來擷取任何已完成的類型定義，也就是已載入的類型。  
  
 指定陣列陣序即可存取反映中的陣列：  
  
-   `Type.GetType("MyArray[]")` 會取得下限為 0 的一維陣列。  
  
-   `Type.GetType("MyArray[*]")` 會取得下限不明的一維陣列。  
  
-   `Type.GetType("MyArray[][]")` 會取得二維陣列的陣列。  
  
-   `Type.GetType("MyArray[*,*]")` 和 `Type.GetType("MyArray[,]")` 會取得下限不明的矩形二維陣列。  
  
 請注意，就執行階段而言是 `MyArray[] != MyArray[*]`，但對多維陣列而言，兩種標記法是一樣的。 亦即 `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` 評估為 **true**。  
  
 對 **ModuleBuilder.GetType** 而言，`MyArray[0..5]` 表示大小 6、下限 0 的一維陣列。 `MyArray[4…]` 表示大小不明、下限 4 的一維陣列。  
  
<a id="see-also" class="xliff"></a>

## 另請參閱  
 <xref:System.Reflection.AssemblyName>   
 <xref:System.Reflection.Emit.ModuleBuilder>   
 <xref:System.Reflection.Emit.TypeBuilder>   
 <xref:System.Type.FullName%2A?displayProperty=fullName>   
 <xref:System.Type.GetType%2A?displayProperty=fullName>   
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName>   
 [檢視類型資訊](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
