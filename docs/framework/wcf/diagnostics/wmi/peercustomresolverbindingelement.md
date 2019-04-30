---
title: PeerCustomResolverBindingElement
ms.date: 03/30/2017
ms.assetid: 9ccc2770-a20e-4dff-9970-f56ad8aec2b5
ms.openlocfilehash: c7f8fd23133cd83ad87a00134b9755b94f531d8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963055"
---
# <a name="peercustomresolverbindingelement"></a>PeerCustomResolverBindingElement

PeerCustomResolverBindingElement

## <a name="syntax"></a>語法

```csharp
class PeerCustomResolverBindingElement : PeerResolverBindingElement
{
    string Address;
    string Binding;
};
```

## <a name="methods"></a>方法

PeerCustomResolverBindingElement 類別不會定義任何方法。

## <a name="properties"></a>屬性

 PeerCustomResolverBindingElement 類別有下列屬性：

### <a name="address"></a>地址

資料型別：字串

存取類型：唯讀

對等自訂解析程式的位址。

### <a name="binding"></a>繫結

資料型別：字串

存取類型：唯讀

繫結的組態名稱。

## <a name="requirements"></a>需求

|MOF|於 Servicemodel.mof 中宣告。|
|---------|-----------------------------------|
|命名空間|於 root\ServiceModel 中定義|

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement>
