---
title: Protobuf 適用于 variant 類型的 Any 和一個欄位-WCF 開發人員的 gRPC
description: 瞭解如何使用 Any 型別和一個關鍵字來代表訊息中的 variant 物件類型。
ms.date: 09/09/2019
ms.openlocfilehash: 6fe7acbd1ec35289f7ad6f3acee8509ab934619d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543192"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="88349-103">Protobuf variant 類型的 Any 和一個欄位</span><span class="sxs-lookup"><span data-stu-id="88349-103">Protobuf Any and Oneof fields for variant types</span></span>

<span data-ttu-id="88349-104">在 Windows Communication Foundation （WCF）中處理動態屬性類型（也就是類型 `object`的屬性）會很複雜。</span><span class="sxs-lookup"><span data-stu-id="88349-104">Handling dynamic property types (that is, properties of type `object`) in Windows Communication Foundation (WCF) is complicated.</span></span> <span data-ttu-id="88349-105">例如，您必須指定序列化程式並提供[KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="88349-105">For example, you must specify serializers and provide [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes.</span></span>

<span data-ttu-id="88349-106">通訊協定緩衝區（Protobuf）提供兩個較簡單的選項，可用來處理可能屬於一種以上類型的值。</span><span class="sxs-lookup"><span data-stu-id="88349-106">Protocol Buffer (Protobuf) provides two simpler options for dealing with values that might be of more than one type.</span></span> <span data-ttu-id="88349-107">`Any` 型別可以代表任何已知的 Protobuf 訊息型別。</span><span class="sxs-lookup"><span data-stu-id="88349-107">The `Any` type can represent any known Protobuf message type.</span></span> <span data-ttu-id="88349-108">而且您可以使用 `oneof` 關鍵字，指定在任何訊息中只能設定一個欄位範圍的其中一個。</span><span class="sxs-lookup"><span data-stu-id="88349-108">And you can use the `oneof` keyword to specify that only one of a range of fields can be set in any message.</span></span>

## <a name="any"></a><span data-ttu-id="88349-109">任意</span><span class="sxs-lookup"><span data-stu-id="88349-109">Any</span></span>

<span data-ttu-id="88349-110">`Any` 是 Protobuf 的「知名型別」之一，這是一組有用、可重複使用的訊息型別，並以所有支援的語言執行。</span><span class="sxs-lookup"><span data-stu-id="88349-110">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="88349-111">若要使用 `Any` 類型，您必須匯入 `google/protobuf/any.proto` 定義。</span><span class="sxs-lookup"><span data-stu-id="88349-111">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

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

<span data-ttu-id="88349-112">在程式C#代碼中，`Any` 類別提供了設定欄位、將訊息解壓縮，以及檢查類型的方法。</span><span class="sxs-lookup"><span data-stu-id="88349-112">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

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

<span data-ttu-id="88349-113">Protobuf 的內部反映程式碼會在每個產生的類型上使用 `Descriptor` 靜態欄位，以解析 `Any` 欄位類型。</span><span class="sxs-lookup"><span data-stu-id="88349-113">Protobuf's internal reflection code uses the `Descriptor` static field on each generated type to resolve `Any` field types.</span></span> <span data-ttu-id="88349-114">另外還有 `TryUnpack<T>` 的方法，但即使失敗，也會建立未初始化的 `T` 實例。</span><span class="sxs-lookup"><span data-stu-id="88349-114">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails.</span></span> <span data-ttu-id="88349-115">如先前所示，最好使用 `Is` 方法。</span><span class="sxs-lookup"><span data-stu-id="88349-115">It's better to use the `Is` method as shown earlier.</span></span>

## <a name="oneof"></a><span data-ttu-id="88349-116">一個</span><span class="sxs-lookup"><span data-stu-id="88349-116">Oneof</span></span>

<span data-ttu-id="88349-117">一個欄位是一種語言功能：編譯器會在產生 message 類別時處理 `oneof` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="88349-117">Oneof fields are a language feature: the compiler handles the `oneof` keyword when it generates the message class.</span></span> <span data-ttu-id="88349-118">使用 `oneof` 來指定 `ChangeNotification` 訊息可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="88349-118">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

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

<span data-ttu-id="88349-119">`oneof` 集內的欄位在整體訊息宣告中必須有唯一的欄位編號。</span><span class="sxs-lookup"><span data-stu-id="88349-119">Fields within the `oneof` set must have unique field numbers in the overall message declaration.</span></span>

<span data-ttu-id="88349-120">當您使用 `oneof`時，產生C#的程式碼會包含列舉，以指定已設定的欄位。</span><span class="sxs-lookup"><span data-stu-id="88349-120">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="88349-121">您可以測試列舉以尋找已設定的欄位。</span><span class="sxs-lookup"><span data-stu-id="88349-121">You can test the enum to find which field is set.</span></span> <span data-ttu-id="88349-122">未設定的欄位會傳回 `null` 或預設值，而不是擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="88349-122">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

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

<span data-ttu-id="88349-123">設定屬於 `oneof` 集之一部分的任何欄位，將會自動清除該集合中的任何其他欄位。</span><span class="sxs-lookup"><span data-stu-id="88349-123">Setting any field that's part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="88349-124">您無法搭配 `oneof`使用 `repeated`。</span><span class="sxs-lookup"><span data-stu-id="88349-124">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="88349-125">相反地，您可以建立具有重複欄位或 `oneof` 設定的嵌套訊息，以解決這項限制。</span><span class="sxs-lookup"><span data-stu-id="88349-125">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="88349-126">[上一頁](protobuf-reserved.md)
>[下一頁](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="88349-126">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
