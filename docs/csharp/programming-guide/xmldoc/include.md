---
title: "&lt;include&gt; (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- include
- <include>
dev_langs:
- CSharp
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: df0438dd742db802bb0f935d840006236d5d9bf9
ms.openlocfilehash: 0cabcc25c4e35027c600e4af2bccfad7f9db1514
ms.contentlocale: zh-tw
ms.lasthandoff: 08/29/2017

---
# <a name="ltincludegt-c-programming-guide"></a>&lt;include&gt; (C# 程式設計手冊)
## <a name="syntax"></a>語法  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a>參數  
 `filename`  
 包含文件的 XML 檔案名稱。 檔案名稱可以使用路徑進行限定。 請將 `filename` 括在單引號 (' ') 內。  
  
 `tagpath`  
 `filename` 中導致 `name` 標記的標記路徑。 請將路徑括在單引號 (' ') 內。  
  
 `name`  
 標記中位在註解前面的名稱規範；`name` 會有 `id`。  
  
 `id`  
 位在註解前面的標記識別碼。 請將識別碼括在雙引號 (" ") 內。  
  
## <a name="remarks"></a>備註  
 \<include> 標記可讓您參考另一個檔案中描述原始程式碼中類型和成員的註解。 這是將文件註解直接放在原始程式碼檔中的替代方案。 將文件放入個別檔案，即可將原始檔控制套用至與原始程式碼不同的文件。 一個人可以簽出原始程式碼檔，而且其他人可以簽出文件檔。  
  
 \<include> 標記使用 XML XPath 語法。 如需自訂 \<include> 用法的方式，請參閱 XPath 文件。  
  
## <a name="example"></a>範例  
 這是多檔案範例。 使用 \<include> 的第一個檔案如下所示：  
  
 [!code-cs[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 第二個檔案 xml_include_tag.doc 包含下列文件註解：  
  
```xml  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## <a name="program-output"></a>程式輸出  
 當您使用下列命令列編譯 Test 和 Test2 類別時，會產生下列輸出：`/doc:DocFileName.xml.`。在 Visual Studio 中，您可以在專案設計工具的 [建置] 窗格中指定 XML 文件註解選項。 當 C# 編譯器看到 \<include> 標記時，會搜尋 xml_include_tag.doc 中的文件註解，而不是目前的原始程式檔。 編譯器接著會產生 DocFileName.xml，這是 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類文件工具用來產生最終文件的檔案。  
  
```xml  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

