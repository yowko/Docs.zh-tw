---
title: Protobuf 訊息-WCF 開發人員的 gRPC
description: '瞭解如何在 IDL 中定義 Protobuf 訊息，以及如何在 c # 中產生。'
ms.date: 12/15/2020
ms.openlocfilehash: c1f2a3071d45dcbe4b98d747f19fed508bad102f
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938100"
---
# <a name="protobuf-messages"></a><span data-ttu-id="d4e6b-103">Protobuf 訊息</span><span class="sxs-lookup"><span data-stu-id="d4e6b-103">Protobuf messages</span></span>

<span data-ttu-id="d4e6b-104">本節說明如何在檔案中 (Protobuf) 訊息來宣告通訊協定緩衝區 `.proto` 。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="d4e6b-105">它會說明欄位編號和類型的基本概念，並查看編譯器產生的 c # 程式碼 `protoc` 。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="d4e6b-106">本章的其餘部分將詳細說明不同類型的資料在 Protobuf 中的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="d4e6b-107">宣告訊息</span><span class="sxs-lookup"><span data-stu-id="d4e6b-107">Declaring a message</span></span>

<span data-ttu-id="d4e6b-108">在 Windows Communication Foundation (WCF) 中， `Stock` 可定義股票市場交易應用程式的類別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d4e6b-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

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

<span data-ttu-id="d4e6b-109">若要在 Protobuf 中執行對等的類別，您必須在檔案中宣告它 `.proto` 。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="d4e6b-110">`protoc`編譯器接著會產生 .net 類別做為組建程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="d4e6b-111">第一行宣告所使用的語法版本。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="d4e6b-112">第3版的語言已于2016發行。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="d4e6b-113">這是我們建議用來 gRPC 服務的版本。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="d4e6b-114">這 `option csharp_namespace` 一行指定要用於產生之 c # 類型的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="d4e6b-115">針對其他語言編譯檔案時，將會忽略此選項 `.proto` 。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="d4e6b-116">Protobuf 檔案通常包含數種語言的特定語言選項。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="d4e6b-117">`Stock`訊息定義會指定四個欄位。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="d4e6b-118">每個都有類型、名稱和欄位編號。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="d4e6b-119">欄位編號</span><span class="sxs-lookup"><span data-stu-id="d4e6b-119">Field numbers</span></span>

<span data-ttu-id="d4e6b-120">欄位號碼是 Protobuf 很重要的一部分。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="d4e6b-121">它們是用來識別二進位編碼資料中的欄位，這表示它們無法從版本變更為您的服務版本。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="d4e6b-122">優點是可以回溯相容性和向前相容性。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="d4e6b-123">用戶端和服務會忽略他們不知道的欄位編號，只要處理遺漏值的可能性即可。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-123">Clients and services will ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="d4e6b-124">在二進位格式中，欄位編號會與類型識別碼合併。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="d4e6b-125">從1到15的欄位編號可以用其類型作為單一位元組進行編碼。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="d4e6b-126">從16到2047的數位需要2個位元組。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="d4e6b-127">如果您基於任何原因需要在訊息上超過2047個欄位，您可以更高的版本。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="d4e6b-128">欄位編號1到15的單一位元組識別碼可提供較佳的效能，因此您應該將它們用於最基本、常用的欄位。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-128">The single-byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="d4e6b-129">類型</span><span class="sxs-lookup"><span data-stu-id="d4e6b-129">Types</span></span>

<span data-ttu-id="d4e6b-130">型別宣告使用 Protobuf 的原生純量資料類型，在 [下一節](protobuf-data-types.md)中會更詳細地討論。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="d4e6b-131">本章的其餘部分將涵蓋 Protobuf 的內建類型，並顯示它們與常見 .NET 類型的關聯性。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="d4e6b-132">Protobuf 原本不支援 `decimal` 型別，因此 `double` 改用。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="d4e6b-133">對於需要完整十進位精確度的應用程式，請參閱本章節下一節中的 [小數區段](protobuf-data-types.md#decimals) 。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="d4e6b-134">產生的程式碼</span><span class="sxs-lookup"><span data-stu-id="d4e6b-134">The generated code</span></span>

<span data-ttu-id="d4e6b-135">當您建立應用程式時，Protobuf 會為每個訊息建立類別，並將其原生類型對應至 c # 類型。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="d4e6b-136">產生的 `Stock` 類型會有下列簽章：</span><span class="sxs-lookup"><span data-stu-id="d4e6b-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="d4e6b-137">產生的實際程式碼遠比這個更複雜許多。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="d4e6b-138">原因是每個類別都包含序列化和還原序列化為二進位電傳格式所需的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="d4e6b-139">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="d4e6b-139">Property names</span></span>

<span data-ttu-id="d4e6b-140">請注意，Protobuf 編譯器會套用 `PascalCase` 至屬性名稱，但它們是 `snake_case` 在檔案中 `.proto` 。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="d4e6b-141">[Protobuf 樣式指南](https://developers.google.com/protocol-buffers/docs/style)建議 `snake_case` 在您的訊息定義中使用，讓其他平臺的程式碼產生產生其慣例的預期大小寫。</span><span class="sxs-lookup"><span data-stu-id="d4e6b-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d4e6b-142">[上一個](protocol-buffers.md) 
>[下一步](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="d4e6b-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
