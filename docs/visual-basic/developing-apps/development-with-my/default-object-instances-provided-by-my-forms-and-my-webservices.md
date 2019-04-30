---
title: My.Forms 和 My.WebServices 提供的預設物件執行個體 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: ca31e1c40c77bf7f42d246019d81f4ffaed646e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014449"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>My.Forms 和 My.WebServices 提供的預設物件執行個體 (Visual Basic)
[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)並[My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)物件提供存取表單、 資料來源和您的應用程式所使用的 XML Web 服務。 其做法是提供的集合*預設執行個體會*的每個物件。  
  
## <a name="default-instances"></a>預設執行個體  
 預設執行個體是執行個體之類別的執行階段所提供，而且不需要是宣告和使用具現化`Dim`和`New`陳述式。 下列範例示範如何您可能會宣告並具現化的執行個體<xref:System.Windows.Forms.Form>類別，稱為`Form1`，以及您為何現在能夠取得的預設執行個體，這個<xref:System.Windows.Forms.Form>類別透過`My.Forms`。  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 `My.Forms`物件傳回的預設執行個體的集合，每個`Form`存在於您的專案中的類別。 同樣地，`My.WebServices`提供針對每個 Web 服務 proxy 類別的預設執行個體，您已在您的應用程式中建立的參考。  
  
## <a name="see-also"></a>另請參閱

- [My.Forms 物件](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.WebServices 物件](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [My 如何相依於專案類型](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
