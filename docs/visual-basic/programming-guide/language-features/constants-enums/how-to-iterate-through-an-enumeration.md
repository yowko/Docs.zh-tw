---
title: 如何：逐一查看列舉
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 21c170d4708b90987a3f1e9c18969b8803fcdbe0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058712"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>如何：在 Visual Basic 中逐一查看列舉類型

列舉提供使用相關常數組和建立常數值與名稱之關聯的便利方法。 若要逐一查看列舉，您可以使用方法將它移到陣列中 <xref:System.Enum.GetValues%2A> 。 您也可以使用語句來逐一查看列舉 `For...Each` ，方法是使用 <xref:System.Enum.GetNames%2A> 或 <xref:System.Enum.GetValues%2A> 方法來解壓縮字串或數值。  
  
### <a name="to-iterate-through-an-enumeration"></a>逐一查看列舉  
  
- 宣告陣列，並使用方法將列舉轉換為它，然後 <xref:System.Enum.GetValues%2A> 再傳遞陣列，就像處理任何其他變數一樣。 下列範例 <xref:Microsoft.VisualBasic.FirstDayOfWeek> 會在逐一查看列舉時，顯示列舉的每個成員。  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>另請參閱

- [列舉的概觀](enumerations-overview.md)
- [如何：宣告列舉類型](how-to-declare-enumerations.md)
- [何時使用列舉類型](when-to-use-an-enumeration.md)
- [如何：決定與列舉值相關聯的字串](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [如何：參考列舉類型成員](how-to-refer-to-an-enumeration-member.md)
- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [陣列](../arrays/index.md)
