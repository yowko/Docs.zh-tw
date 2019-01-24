---
title: 以 SerializationBinder 控制序列化與還原序列化
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 518a9bc88dd291f608f736a47a107549e399eb94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629497"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>以 SerializationBinder 控制序列化與還原序列化
在序列化期間，格式器會傳輸在建立正確型別和版本之物件執行個體時的必要資訊。 這項資訊通常包含物件的完整型別名稱和組件名稱。 根據預設，還原序列化會使用這項資訊建立完全相同物件的執行個體。 某些使用者可能因為執行還原序列化的電腦上不存在原始類別、原始類別已在組件之間移動，或是伺服器和用戶端上需要不同版本的類別，而需要控制要序列化和還原序列化的類別。 如需詳細資訊，請參閱 <<c0> [ 使用狀況的序列化繫結器](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)。  
  
> [!WARNING]
>  此功能只有在使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 或 <xref:System.Runtime.Serialization.NetDataContractSerializer> 時才能使用。  
  
## <a name="using-serializationbinder"></a>使用 SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder> 是抽象類別，用來控制序列化和還原序列化期間使用的實際型別。 若要控制序列化和還原序列化期間使用的型別，請從 <xref:System.Runtime.Serialization.SerializationBinder> 衍生類別，並且覆寫 <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> 和 <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> 方法。 <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> 方法會採用 <xref:System.Type>，並且傳回組件和型別名稱。 <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> 方法會採用組件和型別名稱，並傳回 <xref:System.Type>。  
  
## <a name="see-also"></a>另請參閱
- [序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)
- [使用序列化繫結器](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
