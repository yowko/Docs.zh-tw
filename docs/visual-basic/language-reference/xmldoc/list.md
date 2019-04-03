---
title: <list> (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 7d7b85867f4c701322c5e6c31f2d89ab38fad05d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818525"
---
# <a name="list-visual-basic"></a>\<清單 > (Visual Basic)
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
  
## <a name="parameters"></a>參數  
 `type`  
 清單的類型。 必須是"bullet"項目符號清單、 編號的清單，或兩個資料行資料表的 「 資料表 」 的 「 數字 」。  
  
 `term`  
 僅當使用`type`是 「 資料表 」。 要定義的詞彙，描述標記中定義。  
  
 `description`  
 當`type`"bullet"或"number"、`description`清單中的項目時`type`是 「 資料表 」`description`定義`term`。  
  
## <a name="remarks"></a>備註  
 `<listheader>`區塊會定義資料表或定義清單的標題。 當定義資料表，您只需要提供的項目`term`標題中。  
  
 在清單中的每個項目指定`<item>`區塊。 在建立時定義 清單中，您必須同時指定`term`和`description`。 不過，針對資料表、 項目符號清單中或編號的清單中，您只需要提供的項目`description`。  
  
 清單或資料表可以有多個`<item>`封鎖所需。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<list>`標記來定義項目符號清單中的 < 備註 > 一節。  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)
