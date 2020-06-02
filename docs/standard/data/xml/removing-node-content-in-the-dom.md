---
title: 移除 DOM 中的節點內容
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: 02737c5b680321392d93d785b757c58f2b8da9ee
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288650"
---
# <a name="removing-node-content-in-the-dom"></a>移除 DOM 中的節點內容
針對繼承自 <xref:System.Xml.XmlCharacterData> 的 <xref:System.Xml.XmlComment>、<xref:System.Xml.XmlText>、<xref:System.Xml.XmlCDataSection>、<xref:System.Xml.XmlWhitespace> 及 <xref:System.Xml.XmlSignificantWhitespace> 節點型別，您可使用 <xref:System.Xml.XmlCharacterData.DeleteData%2A> 方法移除字元，該方法會移除節點中的字元範圍。 若要完全移除內容，可以移除包含內容的節點。 若要保留內容不正確的節點，應修改該節點的內容。 如需修改節點內容的詳細資訊，請參閱[修改 XML 文件中的節點、內容和值](modifying-nodes-content-and-values-in-an-xml-document.md)。  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](xml-document-object-model-dom.md)
