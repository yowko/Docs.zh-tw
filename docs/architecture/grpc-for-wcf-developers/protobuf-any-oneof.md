---
title: Protobuf 適用于 variant 類型的 Any 和一個欄位-WCF 開發人員的 gRPC
description: 瞭解如何使用 Any 型別和一個關鍵字來代表訊息中的 variant 物件類型。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 9e730e96bfdb25ef6e07ee10967921408c6f2e84
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184278"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="32d4f-103">Protobuf variant 類型的 Any 和一個欄位</span><span class="sxs-lookup"><span data-stu-id="32d4f-103">Protobuf Any and Oneof fields for variant types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="32d4f-104">在 WCF 中處理動態屬性類型（也就是`object`類型的屬性）很複雜。</span><span class="sxs-lookup"><span data-stu-id="32d4f-104">Handling dynamic property types (that is, properties of type `object`) in WCF is complicated.</span></span> <span data-ttu-id="32d4f-105">必須指定序列化程式，必須提供[KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute)屬性，依此類推。</span><span class="sxs-lookup"><span data-stu-id="32d4f-105">Serializers must be specified, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes must be provided, and so on.</span></span>

<span data-ttu-id="32d4f-106">Protobuf 提供兩個較簡單的選項，可處理可能屬於一種以上類型的值。</span><span class="sxs-lookup"><span data-stu-id="32d4f-106">Protobuf provides two simpler options for dealing with values that may be of more than one type.</span></span> <span data-ttu-id="32d4f-107">型別可以代表任何已知的 Protobuf 訊息型別， `oneof`而關鍵字可讓您指定在任何指定的訊息中只能設定一個欄位範圍的其中一個。 `Any`</span><span class="sxs-lookup"><span data-stu-id="32d4f-107">The `Any` type can represent any known Protobuf message type, while the `oneof` keyword allows you to specify that only one of a range of fields can be set in any given message.</span></span>

## <a name="any"></a><span data-ttu-id="32d4f-108">Any</span><span class="sxs-lookup"><span data-stu-id="32d4f-108">Any</span></span>

<span data-ttu-id="32d4f-109">`Any`是 Protobuf 的「知名型別」之一，這是一組有用、可重複使用的訊息型別，並以所有支援的語言執行。</span><span class="sxs-lookup"><span data-stu-id="32d4f-109">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="32d4f-110">若要使用`Any`類型，您必須匯`google/protobuf/any.proto`入定義。</span><span class="sxs-lookup"><span data-stu-id="32d4f-110">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

```protobuf
syntax "proto3"

import "google/protobuf/any.proto"

message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
    int32 id = 1;
    google.protobuf.Any instrument = 2;
}
```

<span data-ttu-id="32d4f-111">在程式C#代碼中， `Any`類別會提供方法來設定欄位、將訊息解壓縮，以及檢查類型。</span><span class="sxs-lookup"><span data-stu-id="32d4f-111">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    if (change.Instrument.Is(Stock.Descriptor))
    {
        FormatStock(change.Instrument.Unpack<Stock>());
    }
    else if (change.Instrument.Is(Currency.Descriptor))
    {
        FormatCurrency(change.Instrument.Unpack<Currency>());
    }
    else
    {
        throw new ArgumentException("Unknown instrument type");
    }
}
```

<span data-ttu-id="32d4f-112">Protobuf `Descriptor`的內部反映程式碼會使用每個產生之類型上的靜態欄位`Any`來解析欄位類型。</span><span class="sxs-lookup"><span data-stu-id="32d4f-112">The `Descriptor` static field on each generated type is used by Protobuf's internal reflection code to resolve `Any` field types.</span></span> <span data-ttu-id="32d4f-113">另外還有`TryUnpack<T>`方法，但即使失敗，也會建立未初始化`T`的實例，因此最好使用`Is`方法，如上所示。</span><span class="sxs-lookup"><span data-stu-id="32d4f-113">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails, so it's better to use the `Is` method as shown above.</span></span>

## <a name="oneof"></a><span data-ttu-id="32d4f-114">一個</span><span class="sxs-lookup"><span data-stu-id="32d4f-114">Oneof</span></span>

<span data-ttu-id="32d4f-115">一個欄位是一種語言功能： `oneof`編譯器會在產生 message 類別時處理關鍵字。</span><span class="sxs-lookup"><span data-stu-id="32d4f-115">Oneof fields are a language feature: the `oneof` keyword is handled by the compiler when it generates the message class.</span></span> <span data-ttu-id="32d4f-116">使用`oneof` 來`ChangeNotification`指定訊息可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="32d4f-116">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

```protobuf
message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
  int32 id = 1;
  oneof instrument {
    Stock stock = 2;
    Currency currency = 3;
  }
}
```

<span data-ttu-id="32d4f-117">`oneof`集合內的欄位在整體訊息宣告中必須有唯一的欄位編號。</span><span class="sxs-lookup"><span data-stu-id="32d4f-117">Fields within the `oneof` set must have unique field numbers within the overall message declaration.</span></span>

<span data-ttu-id="32d4f-118">當您使用`oneof`時，產生C#的程式碼會包含列舉，以指定已設定的欄位。</span><span class="sxs-lookup"><span data-stu-id="32d4f-118">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="32d4f-119">您可以測試列舉以尋找已設定的欄位。</span><span class="sxs-lookup"><span data-stu-id="32d4f-119">You can test the enum to find which field is set.</span></span> <span data-ttu-id="32d4f-120">未設定的欄位會`null`傳回或預設值，而不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="32d4f-120">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    switch (change.InstrumentCase)
    {
        case ChangeNotification.InstrumentOneofCase.None:
            return;
        case ChangeNotification.InstrumentOneofCase.Stock:
            FormatStock(change.Stock);
            break;
        case ChangeNotification.InstrumentOneofCase.Currency:
            FormatCurrency(change.Currency);
            break;
        default:
            throw new ArgumentException("Unknown instrument type");
    }
}
```

<span data-ttu-id="32d4f-121">設定屬於`oneof`集合之一部分的任何欄位，將會自動清除該集合中的任何其他欄位。</span><span class="sxs-lookup"><span data-stu-id="32d4f-121">Setting any field that is part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="32d4f-122">您無法搭配`repeated`使用`oneof`。</span><span class="sxs-lookup"><span data-stu-id="32d4f-122">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="32d4f-123">相反地，您可以建立具有重複欄位或`oneof`集合的嵌套訊息，以解決這項限制。</span><span class="sxs-lookup"><span data-stu-id="32d4f-123">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="32d4f-124">[上一頁](protobuf-reserved.md)
>[下一頁](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="32d4f-124">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
