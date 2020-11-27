---
title: 作法：建立類別或結構的基本資料合約
description: 遵循此範例以瞭解如何使用 DataContractAttribute 屬性，在 WCF 中使用類別或結構來建立資料合約。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 5634eb3d3ec18d95fd7d6b3c89b572ab4f5b8eca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254034"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>作法：建立類別或結構的基本資料合約

本主題將示範使用類別或結構來建立資料合約的基本步驟。 如需資料合約和其使用方式的詳細資訊，請參閱 [使用資料合約](using-data-contracts.md)。  
  
 如需逐步解說建立基本 Windows Communication Foundation (WCF) 服務和用戶端之步驟的教學課程，請參閱 [消費者入門教學](../getting-started-tutorial.md)課程。 如需包含基本服務和用戶端的實用範例應用程式，請參閱 [基本資料合約](../samples/basic-data-contract.md)。  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>建立類別或結構的基本資料合約  
  
1. 請將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至類別，以宣告型別具有資料合約。 請注意，所有公用型別 (包括不含屬性的公用型別) 都是可序列化的。 如果沒有 <xref:System.Runtime.Serialization.DataContractSerializer> 屬性，<xref:System.Runtime.Serialization.DataContractAttribute> 會推斷資料合約。 如需詳細資訊，請參閱可序列化的 [類型](serializable-types.md)。  
  
2. 藉由將 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Attribute) 套用至各個成員，定義序列化的成員 (屬性 (Property)、欄位或事件)。 這些成員稱為資料成員。 根據預設，所有公用型別都是可序列化的。 如需詳細資訊，請參閱可序列化的 [類型](serializable-types.md)。  
  
    > [!NOTE]
    > 您可以將 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性套用至私用欄位，造成資料對他人公開。 請確定成員沒有包含敏感性資料。  
  
## <a name="example"></a>範例  

 下列範例說明如何將 `Person` 和 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至類別和其成員，以建立 <xref:System.Runtime.Serialization.DataMemberAttribute> 型別的資料合約。  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [使用資料合約](using-data-contracts.md)
- [快速入門教學課程](../getting-started-tutorial.md)
- [快速入門](../samples/getting-started-sample.md)
