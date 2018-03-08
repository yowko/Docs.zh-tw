---
title: "使用 msxsl:script 的指令碼區塊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: badf5511c5638d98d25997f31a3aff8dc11144d6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="script-blocks-using-msxslscript"></a>使用 msxsl:script 的指令碼區塊
<xref:System.Xml.Xsl.XslCompiledTransform> 類別支援使用 `msxsl:script` 項目的內嵌指令碼。 載入樣式表時，程式碼文件物件模型 (CodeDOM) 會將任何已定義的函式編譯成 Microsoft Intermediate Language (MSIL)，並在執行階段期間執行。 從內嵌指令碼區塊產生的組件不同於為樣式表產生的組件。  
  
## <a name="enable-xslt-script"></a>啟用 XSLT 指令碼  
 內嵌指令碼支援是 <xref:System.Xml.Xsl.XslCompiledTransform> 類別上的選擇性 XSLT 設定。 預設會停用指令碼支援。 若要啟用指令碼支援，請建立 <xref:System.Xml.Xsl.XsltSettings> 物件 (將 <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> 屬性設為 `true`)，並將該物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 方法。  
  
> [!NOTE]
>  僅當需要指令碼支援且在完全受信任的環境中運作時，才應啟用 XSLT 指令碼。  
  
## <a name="msxslscript-element-definition"></a>msxsl:script 項目定義  
 `msxsl:script` 項目是 XSLT 1.0 版建議事項的 Microsoft 擴充功能，其定義如下：  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 `msxsl` 前置詞會繫結至 `urn:schemas-microsoft-com:xslt` 命名空間 URI。 樣式表必須包括 `xmlns:msxsl=urn:schemas-microsoft-com:xslt` 命名空間宣告。  
  
 `language` 屬性是選擇性的。 其值是內嵌程式碼區塊的程式碼語言。 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> 方法，可將該語言對應至適當的 CodeDOM 編譯器。 <xref:System.Xml.Xsl.XslCompiledTransform> 類別可支援任何 Microsoft .NET 語言 (假設機器上已安裝適當的提供者，且已註冊到 machine.config 檔案的 system.codedom 區段中)。 如果沒有指定 `language` 屬性，語言預設為 JScript。 語言名稱不區分大小寫，因此 JavaScript 與 javascript 是一樣的。  
  
 `implements-prefix` 屬性是必要的。 這個屬性用來宣告命名空間，並把它與指令碼區塊產生關聯。 這個屬性的值是表示命名空間的前置詞。 這個前置詞可以被定義在樣式表內的任意處。  
  
> [!NOTE]
>  使用 `msxsl:script` 項目時，無論所使用的語言為何，都強烈建議將指令碼置於 CDATA 區段內。 因為指令碼可能包含給定語言的運算子、識別項或分隔符號，所以如果未包含在 CDATA 區段中，則有可能會錯誤解譯為 XML。 下列 XML 顯示可將程式碼放置其中的 CDATA 區段範本。  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a>指令碼函式  
 函式可在 `msxsl:script` 項目內進行宣告。 宣告函式時，函式是包含在指令碼區塊內。 樣式表可以包含多個指令碼區塊，而每一個都會各自獨立運作。 這表示如果您在指令碼區塊內執行，您無法呼叫在另一個指令碼區塊內所定義的函式，除非它被宣告成有相同的命名空間和相同的指令碼語言。 因為每一個指令碼區塊都可以使用本身的語言，且這些區塊是根據該語言剖析器的文法規則進行剖析，建議您針對使用中的語言使用正確的語法。 例如，如果是 Microsoft C# 指令碼區塊，請使用 C# 註解語法。  
  
 提供給函式的引數及傳回值可具有任何類型。 因為 W3C XPath 類型是 Common Language Runtime (CLR) 類型的子集，所以當系統認為某類型不是 XPath 類型時，便會進行類型轉換。 下表顯示對應的 W3C 類型與對等的 CLR 類型。  
  
|W3C 類型|CLR 類型|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 CLR 數字類型會轉換為 <xref:System.Double>。 <xref:System.DateTime> 類型會轉換為 <xref:System.String>。 <xref:System.Xml.XPath.IXPathNavigable> 類型會轉換為 <xref:System.Xml.XPath.XPathNavigator>。 **XPathNavigator[]** 會轉換為 <xref:System.Xml.XPath.XPathNodeIterator>。  
  
 所有其他類型都會擲回錯誤。  
  
### <a name="importing-namespaces-and-assemblies"></a>匯入命名空間及組件  
 <xref:System.Xml.Xsl.XslCompiledTransform> 類別會預先定義一組預設 `msxsl:script` 項目所支援的命名空間及組件。 不過，透過將組件及命名空間匯入 `msxsl:script` 區塊，也可以使用屬於不在預先定義清單上之命名空間的類別及成員。  
  
#### <a name="assemblies"></a>組件  
 預設會參考下列兩個組件：  
  
-   System.dll  
  
-   System.Xml.dll  
  
-   Microsoft.VisualBasic.dll (若指令碼語言為 VB)  
  
 您可以使用 `msxsl:assembly` 項目匯入其他組件。 編譯樣式表時會併入該組件。 `msxsl:assembly` 項目具有下列定義：  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 `name` 屬性包含組件名稱，而 `href` 屬性則包含組件的路徑。 組件名稱可為完整名稱 (如 "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089") 或簡短名稱 (如 "System.Web")。  
  
#### <a name="namespaces"></a>命名空間  
 預設會包含下列命名空間：  
  
-   系統  
  
-   System.Collection  
  
-   System.Text  
  
-   System.Text.RegularExpressions  
  
-   System.Xml  
  
-   System.Xml.Xsl  
  
-   System.Xml.XPath  
  
-   Microsoft.VisualBasic (若指令碼語言為 VB)  
  
 您可使用 `namespace` 屬性加入對其他命名空間的支援。 屬性值是命名空間的名稱。  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a>範例  
 下列範例會使用內嵌指令碼來計算圓周 (假設已經知道其半徑)。  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a>number.xml  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a>calc.xsl  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a>輸出  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>  
```  
  
## <a name="see-also"></a>請參閱  
 [XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [動態原始程式碼的產生和編譯](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
