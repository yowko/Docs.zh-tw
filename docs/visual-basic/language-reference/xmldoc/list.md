---
title: "&lt;清單&gt;(Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34347df88f1bc3097db0020526ec99943c8f7bd4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltlistgt-visual-basic"></a>&lt;清單&gt;(Visual Basic)
定義清單或資料表。  
  
## <a name="syntax"></a>語法  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 清單的類型。 必須是"bullet"項目符號清單、 「 數字 」 編號的清單，或"table"的兩個資料行的資料表。  
  
 `term`  
 僅當使用`type`是 「 資料表 」。 若要定義，詞彙描述標記中定義。  
  
 `description`  
 當`type`"bullet"或""`description`是清單中的項目時`type`是"table"`description`的定義`term`。  
  
## <a name="remarks"></a>備註  
 `<listheader>`區塊會定義表格或定義清單的標題。 當定義資料表，您只需要提供的項目`term`標題中。  
  
 在清單中的每個項目指定`<item>`區塊。 在建立時定義清單，您必須同時指定`term`和`description`。 不過，針對資料表、 項目符號清單或編號的清單中，您只需要提供的項目`description`。  
  
 清單或資料表中可以有`<item>`視會封鎖。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<list>`標記來定義項目符號清單中的 < 備註 > 一節。  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
