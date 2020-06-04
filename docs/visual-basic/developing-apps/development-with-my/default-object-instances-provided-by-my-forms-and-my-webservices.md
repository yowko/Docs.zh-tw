---
title: My.Forms 及 My.WebServices 提供的預設物件執行個體
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 847724450ee2bc8bc591371f71171e8ba4ed9337
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411736"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>My.Forms 和 My.WebServices 提供的預設物件執行個體 (Visual Basic)

[WebServices](../../language-reference/objects/my-webservices-object.md)物件可讓您存取應用程式所[使用的窗](../../language-reference/objects/my-forms-object.md)體、資料來源和 XML Web Service。 他們會藉由提供每個物件的*預設實例*集合來執行這項操作。  
  
## <a name="default-instances"></a>預設實例  

 預設實例是執行時間所提供之類別的實例，不需要使用和語句來宣告和具現化 `Dim` `New` 。 下列範例示範您可能已經宣告並具現化類別的實例 <xref:System.Windows.Forms.Form> ，而 `Form1` 您現在可以透過取得這個類別的預設實例 <xref:System.Windows.Forms.Form> `My.Forms` 。  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 `My.Forms`物件會針對存在於專案中的每個類別，傳回預設實例的集合 `Form` 。 同樣地， `My.WebServices` 為您在應用程式中建立參考的每個 Web 服務，提供 proxy 類別的預設實例。  
  
## <a name="see-also"></a>另請參閱

- [My.Forms 物件](../../language-reference/objects/my-forms-object.md)
- [My.WebServices 物件](../../language-reference/objects/my-webservices-object.md)
- [My 與專案類型的相依關係](how-my-depends-on-project-type.md)
