---
title: Protobuf 訊息-WCF 開發人員的 gRPC
description: 瞭解 Protobuf 訊息如何定義于 IDL 中，以及如何在C#中產生。
ms.date: 09/09/2019
ms.openlocfilehash: c7375bafb7572b0eaa0458b0310a0114e3fd078c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543036"
---
# <a name="protobuf-messages"></a><span data-ttu-id="1f6ab-103">Protobuf 訊息</span><span class="sxs-lookup"><span data-stu-id="1f6ab-103">Protobuf messages</span></span>

<span data-ttu-id="1f6ab-104">本節涵蓋如何在 `.proto` 檔案中宣告通訊協定緩衝區（Protobuf）訊息。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="1f6ab-105">它會說明欄位編號和類型的基本概念，並查看 `protoc` 編譯器所C#產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span> 

<span data-ttu-id="1f6ab-106">本章的其餘部分將詳細說明 Protobuf 中不同類型資料的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="1f6ab-107">宣告訊息</span><span class="sxs-lookup"><span data-stu-id="1f6ab-107">Declaring a message</span></span>

<span data-ttu-id="1f6ab-108">在 Windows Communication Foundation （WCF）中，股票市場貿易應用程式的 `Stock` 類別可能會如下列範例所定義：</span><span class="sxs-lookup"><span data-stu-id="1f6ab-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

<span data-ttu-id="1f6ab-109">若要在 Protobuf 中執行對等的類別，您必須在 `.proto` 檔案中宣告它。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="1f6ab-110">然後 `protoc` 編譯器會在組建程式中產生 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="1f6ab-111">第一行會宣告所使用的語法版本。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="1f6ab-112">語言的第3版已于2016發行。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="1f6ab-113">這是我們建議的 gRPC 服務版本。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="1f6ab-114">`option csharp_namespace` 行指定要用於產生C#之類型的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="1f6ab-115">針對其他語言編譯 `.proto` 檔案時，將會忽略此選項。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="1f6ab-116">Protobuf 檔案通常包含數種語言的語言特定選項。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="1f6ab-117">`Stock` 訊息定義會指定四個欄位。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="1f6ab-118">每個都有類型、名稱和欄位編號。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="1f6ab-119">欄位編號</span><span class="sxs-lookup"><span data-stu-id="1f6ab-119">Field numbers</span></span>

<span data-ttu-id="1f6ab-120">欄位編號是 Protobuf 中很重要的一部分。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="1f6ab-121">它們是用來識別二進位編碼資料中的欄位，這表示它們無法從版本變更為您的服務版本。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="1f6ab-122">優點是可以回溯相容性和向前相容性。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="1f6ab-123">用戶端和服務只會略過不知道的欄位編號，只要處理遺漏值的可能性即可。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="1f6ab-124">在二進位格式中，欄位編號會與類型識別碼結合。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="1f6ab-125">從1到15的欄位可以用其類型編碼為單一位元組。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="1f6ab-126">從16到2047的數位需要2個位元組。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="1f6ab-127">如果因任何原因而需要訊息超過2047個欄位，您就可以更高。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="1f6ab-128">欄位編號1到15的單一位元組識別碼提供較佳的效能，因此您應該將它們用於最基本、常用的欄位。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="1f6ab-129">類型</span><span class="sxs-lookup"><span data-stu-id="1f6ab-129">Types</span></span>

<span data-ttu-id="1f6ab-130">類型宣告使用 Protobuf 的原生純量資料類型，將在[下一節](protobuf-data-types.md)中更詳細地討論。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="1f6ab-131">本章的其餘部分將涵蓋 Protobuf 的內建型別，並說明它們與常見 .NET 類型的關聯性。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="1f6ab-132">Protobuf 原本就不支援 `decimal` 型別，所以改為使用 `double`。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="1f6ab-133">對於需要完整十進位數精確度的應用程式，請參閱本章下一節中的[小數章節](protobuf-data-types.md#decimals)。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="1f6ab-134">產生的程式碼</span><span class="sxs-lookup"><span data-stu-id="1f6ab-134">The generated code</span></span>

<span data-ttu-id="1f6ab-135">當您建立應用程式時，Protobuf 會為您的每個訊息建立類別，並將C#其原生類型對應至類型。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="1f6ab-136">產生的 `Stock` 類型會具有下列簽章：</span><span class="sxs-lookup"><span data-stu-id="1f6ab-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="1f6ab-137">產生的實際程式碼遠比這個複雜。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="1f6ab-138">原因是每個類別都包含將本身序列化和還原序列化為二進位電傳格式所需的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="1f6ab-139">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="1f6ab-139">Property names</span></span>

<span data-ttu-id="1f6ab-140">請注意，Protobuf 編譯器 `PascalCase` 套用至屬性名稱，雖然它們 `snake_case` 在 `.proto` 檔中。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="1f6ab-141">[Protobuf 樣式指南](https://developers.google.com/protocol-buffers/docs/style)會建議在您的訊息定義中使用 `snake_case`，讓其他平臺的程式碼產生會針對其慣例產生預期的大小寫。</span><span class="sxs-lookup"><span data-stu-id="1f6ab-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1f6ab-142">[上一頁](protocol-buffers.md)
>[下一頁](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="1f6ab-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
