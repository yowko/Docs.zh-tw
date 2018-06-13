---
title: 建立新節點時 XML 項目和屬性名稱的驗證
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de11c190310dec90bd23d044f77d0c38e3a34fcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568845"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>建立新節點時 XML 項目和屬性名稱的驗證
XML 文件物件模型 (DOM) 在建立新項目節點或屬性節點時會檢查名稱的有效性。 如果名稱包含不合法字元，則會擲回例外狀況。 若要確保名稱是有效的且被正確編碼，您必須使用 **XmlConvert** 類別在應用程式層級來編碼名稱並且將它解碼。 **XmlWriter** 有方法來執行其他工作，以確保會產生格式正確的 XML。  
  
## <a name="see-also"></a>請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
