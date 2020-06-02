---
title: 建立新節點時 XML 項目和屬性名稱的驗證
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 1da893261b35c6b57c4f08eb53b7701ec1d81fae
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289846"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>建立新節點時 XML 項目和屬性名稱的驗證
XML 文件物件模型 (DOM) 在建立新項目節點或屬性節點時會檢查名稱的有效性。 如果名稱包含不合法字元，則會擲回例外狀況。 若要確保名稱是有效的且被正確編碼，您必須使用 **XmlConvert** 類別在應用程式層級來編碼名稱並且將它解碼。 **XmlWriter** 有方法來執行其他工作，以確保會產生格式正確的 XML。  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](xml-document-object-model-dom.md)
