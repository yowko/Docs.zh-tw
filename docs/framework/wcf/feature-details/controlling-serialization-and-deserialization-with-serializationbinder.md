---
title: "以 SerializationBinder 控制序列化與還原序列化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c3180d62824f94e27e02c80e09fdf32252f0a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>以 SerializationBinder 控制序列化與還原序列化
在序列化期間，格式器會傳輸在建立正確型別和版本之物件執行個體時的必要資訊。 這項資訊通常包含物件的完整型別名稱和組件名稱。 根據預設，還原序列化會使用這項資訊建立完全相同物件的執行個體。 某些使用者可能因為執行還原序列化的電腦上不存在原始類別、原始類別已在組件之間移動，或是伺服器和用戶端上需要不同版本的類別，而需要控制要序列化和還原序列化的類別。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][序列化繫結器的使用方式](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)。  
  
> [!WARNING]
>  此功能只有在使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 或 <xref:System.Runtime.Serialization.NetDataContractSerializer> 時才能使用。  
  
## <a name="using-serializationbinder"></a>使用 SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder> 是抽象類別，用來控制序列化和還原序列化期間使用的實際型別。 若要控制序列化和還原序列化期間使用的型別，衍生自<xref:System.Runtime.Serialization.SerializationBinder>並覆寫<xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A>System.String、 System.String)?qualifyHint=False & autoUpgrade = True 和<xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>System.String)？qualifyHint = False & autoUpgrade = True 的方法。 <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String、 System.String)?qualifyHint=False & autoUpgrade = True 的方法會採用<xref:System.Type>，並傳回組件和類型的名稱。 <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False & autoUpgrade = True 的方法會採用組件和型別名稱，然後傳回<xref:System.Type>。  
  
## <a name="see-also"></a>另請參閱  
 [序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [序列化繫結器的使用方式](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
