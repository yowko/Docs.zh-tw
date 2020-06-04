---
title: <list>
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
ms.openlocfilehash: 955c1a4c5c5619f908b8d03dbf12360c23574478
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400082"
---
# <a name="list-visual-basic"></a>\<list> (Visual Basic)
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
 清單的類型。 必須是項目符號清單的「專案符號」、編號清單的「數位」，或是兩個數據行資料表的「資料表」。  
  
 `term`  
 只有在 `type` 為 "table" 時才會使用。 要定義的詞彙，定義于 description 標記中。  
  
 `description`  
 當 `type` 為 "table" 或 "number" 時，是清單中的專案，而是的 `description` `type` `description` 定義 `term` 。  
  
## <a name="remarks"></a>備註  
 `<listheader>`區塊會定義資料表或定義清單的標題。 定義資料表時，您只需要在標題中提供的專案 `term` 。  
  
 清單中的每個專案都是以 `<item>` 區塊來指定。 建立定義清單時，您必須同時指定 `term` 和 `description` 。 不過，針對資料表、項目符號清單或編號清單，您只需要提供的專案 `description` 。  
  
 清單或資料表可以視需要擁有多個 `<item>` 區塊。  
  
 使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<list>` 標記來定義 [備註] 區段中的項目符號清單。  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)
