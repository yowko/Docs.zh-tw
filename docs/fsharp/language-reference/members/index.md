---
title: "成員 (F#)"
description: "深入了解 F # 程式語言中的物件成員。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e472f50a-4939-4e62-abbc-471f8f265790
ms.openlocfilehash: ca34c8d073594791ec268a85ad56f50cc6d9e435
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="members"></a>Members

本節描述 F# 物件類型的成員。


## <a name="remarks"></a>備註
「成員」是作為類型定義的一部分且以 `member` 關鍵字宣告的功能。 F# 物件類型 (例如記錄、類別、差別聯集、介面和結構) 支援成員。 如需詳細資訊，請參閱[記錄](../records.md)、[類別](../classes.md)、[差別聯集](../discriminated-Unions.md)、[介面](../interfaces.md)和[結構](../structures.md)。

成員一般構成類型的公用介面，因此除非另外指定，否則成員為公用。 成員也可以宣告為私用或內用。 如需詳細資訊，請參閱[存取控制](../access-Control.md)。 類型的簽章也可以用來公開或不公開類型的特定成員。 如需詳細資訊，請參閱[簽章](../signatures.md)。

只與類別搭配使用的私用欄位和 `do` 繫結，並不是真正的成員，因為它們永遠不是類型之公用介面的一部分，也不是以 `member` 關鍵字宣告，但本節中也會加以描述。


## <a name="related-topics"></a>相關主題


|主題|描述|
|-----|-----------|
|[類別中的 `let` 繫結](let-bindings-in-classes.md)|描述類別中私用欄位和函式的定義。|
|[類別中的 `do` 繫結](do-bindings-in-classes.md)|描述物件初始設定程式碼的規格。|
|[屬性](properties.md)|描述類別和其他類型中的屬性成員。|
|[索引屬性](indexed-properties.md)|描述類別和其他類型中的類似陣列屬性。|
|[方法](methods.md)|描述作為類型成員的函式。|
|[建構函式](constructors.md)|描述初始化型別物件的特殊函式。|
|[運算子多載](../operator-overloading.md)|描述型別之自訂運算子的定義。|
|[事件](events.md)|描述 F# 中的事件定義和事件處理支援。|
|[明確欄位：`val` 關鍵字](explicit-fields-the-val-keyword.md)|描述類型中未初始化欄位的定義。|
