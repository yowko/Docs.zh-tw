---
title: ".NET 中的字元編碼"
description: ".NET 中的字元編碼"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bce54e41-e9dc-493a-8988-1cbadc340fe8
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: a8f42fa6a37f8de6f13186ea2ac17b2b2ced1601
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="character-encoding-in-net"></a><span data-ttu-id="e80b3-104">.NET 中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="e80b3-104">Character encoding in .NET</span></span>

<span data-ttu-id="e80b3-105">字元是可以用許多不同的方式來表示的抽象實體。</span><span class="sxs-lookup"><span data-stu-id="e80b3-105">Characters are abstract entities that can be represented in many different ways.</span></span> <span data-ttu-id="e80b3-106">字元編碼是一套系統，可將所支援之字元集中的每個字元與代表該字元的特定值配對。</span><span class="sxs-lookup"><span data-stu-id="e80b3-106">A character encoding is a system that pairs each character in a supported character set with some value that represents that character.</span></span> <span data-ttu-id="e80b3-107">例如，摩斯密碼就是一種字元編碼，可將羅馬字母中的每個字元與適合透過電報線路傳輸的點和虛線圖樣配對。</span><span class="sxs-lookup"><span data-stu-id="e80b3-107">For example, Morse code is a character encoding that pairs each character in the Roman alphabet with a pattern of dots and dashes that are suitable for transmission over telegraph lines.</span></span> <span data-ttu-id="e80b3-108">電腦的字元編碼可將所支援之字元集中的每個字元與代表該字元的數值配對。</span><span class="sxs-lookup"><span data-stu-id="e80b3-108">A character encoding for computers pairs each character in a supported character set with a numeric value that represents that character.</span></span> <span data-ttu-id="e80b3-109">字元編碼包含兩個不同的元件：</span><span class="sxs-lookup"><span data-stu-id="e80b3-109">A character encoding has two distinct components:</span></span>

* <span data-ttu-id="e80b3-110">編碼器，可將字元序列轉譯成數值 (位元組) 序列。</span><span class="sxs-lookup"><span data-stu-id="e80b3-110">An encoder, which translates a sequence of characters into a sequence of numeric values (bytes).</span></span>

* <span data-ttu-id="e80b3-111">解碼器，可將位元組序列轉譯成字元序列。</span><span class="sxs-lookup"><span data-stu-id="e80b3-111">A decoder, which translates a sequence of bytes into a sequence of characters.</span></span>

<span data-ttu-id="e80b3-112">字元編碼描述編碼器和解碼器運作時所依據的規則。</span><span class="sxs-lookup"><span data-stu-id="e80b3-112">Character encoding describes the rules by which an encoder and a decoder operate.</span></span> <span data-ttu-id="e80b3-113">例如，[UTF8Encoding](xref:System.Text.UTF8Encoding) 類別描述編碼和解碼 8 位元 Unicode 轉換格式 (UTF-8) 的規則，該格式使用一到四個位元組來表示單一 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-113">For example, the [UTF8Encoding](xref:System.Text.UTF8Encoding) class describes the rules for encoding to, and decoding from, 8-bit Unicode Transformation Format (UTF-8), which uses one to four bytes to represent a single Unicode character.</span></span> <span data-ttu-id="e80b3-114">編碼和解碼也可包含驗證。</span><span class="sxs-lookup"><span data-stu-id="e80b3-114">Encoding and decoding can also include validation.</span></span> <span data-ttu-id="e80b3-115">例如，[UnicodeEncoding](xref:System.Text.UnicodeEncoding) 類別會檢查所有 Surrogate，確定它們是由有效的 Surrogate 字組所組成。</span><span class="sxs-lookup"><span data-stu-id="e80b3-115">For example, the [UnicodeEncoding](xref:System.Text.UnicodeEncoding) class checks all surrogates to make sure they constitute valid surrogate pairs.</span></span> <span data-ttu-id="e80b3-116">(Surrogate 字組是由包含範圍從 U+D800 到 U+DBFF 之字碼指標的字元，後面接著包含範圍從 U+DC00 到 U+DFFF 之字碼指標的字元所組成)。後援策略決定編碼器如何處理無效的字元，或解碼器如何處理無效的位元組。</span><span class="sxs-lookup"><span data-stu-id="e80b3-116">(A surrogate pair consists of a character with a code point that ranges from U+D800 to U+DBFF followed by a character with a code point that ranges from U+DC00 to U+DFFF.) A fallback strategy determines how an encoder handles invalid characters or how a decoder handles invalid bytes.</span></span> 

> [!WARNING]
> <span data-ttu-id="e80b3-117">.NET 編碼類別提供儲存和轉換字元資料的方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-117">The .NET encoding classes provide a way to store and convert character data.</span></span> <span data-ttu-id="e80b3-118">這些類別不應用來儲存字串格式的二進位資料。</span><span class="sxs-lookup"><span data-stu-id="e80b3-118">They should not be used to store binary data in string form.</span></span> <span data-ttu-id="e80b3-119">根據使用的編碼方式，使用編碼類別將二進位資料轉換成字串格式可能會導致未預期的行為，並且產生不正確或損毀的資料。</span><span class="sxs-lookup"><span data-stu-id="e80b3-119">Depending on the encoding used, converting binary data to string format with the encoding classes can introduce unexpected behavior and produce inaccurate or corrupted data.</span></span> <span data-ttu-id="e80b3-120">若要將二進位資料轉換成字串格式，請使用 [Convert.ToBase64String](xref:System.Convert.ToBase64String(System.Byte[])) 方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-120">To convert binary data to a string form, use the [Convert.ToBase64String](xref:System.Convert.ToBase64String(System.Byte[])) method.</span></span> 
 
<span data-ttu-id="e80b3-121">.NET 使用 UTF-16 編碼 (以 [UnicodeEncoding](xref:System.Text.UnicodeEncoding) 類別表示) 來表示字元和字串。</span><span class="sxs-lookup"><span data-stu-id="e80b3-121">.NET uses the UTF-16 encoding (represented by the [UnicodeEncoding](xref:System.Text.UnicodeEncoding) class) to represent characters and strings.</span></span> <span data-ttu-id="e80b3-122">以 Common Language Runtime 為目標的應用程式使用編碼器將 Common Language Runtime 所支援的 Unicode 字元表示對應至其他編碼配置，</span><span class="sxs-lookup"><span data-stu-id="e80b3-122">Applications that target the common language runtime use encoders to map Unicode character representations supported by the common language runtime to other encoding schemes.</span></span> <span data-ttu-id="e80b3-123">並使用解碼器將非 Unicode 編碼的字元對應至 Unicode。</span><span class="sxs-lookup"><span data-stu-id="e80b3-123">They use decoders to map characters from non-Unicode encodings to Unicode.</span></span>

<span data-ttu-id="e80b3-124">本主題包含下列章節：</span><span class="sxs-lookup"><span data-stu-id="e80b3-124">This topic consists of the following sections:</span></span>

* [<span data-ttu-id="e80b3-125">.NET 中的編碼</span><span class="sxs-lookup"><span data-stu-id="e80b3-125">Encodings in .NET</span></span>](#encodings-in-net)

* [<span data-ttu-id="e80b3-126">選取編碼類別</span><span class="sxs-lookup"><span data-stu-id="e80b3-126">Selecting an encoding class</span></span>](#selecting-an-encoding-class)

* [<span data-ttu-id="e80b3-127">使用編碼物件</span><span class="sxs-lookup"><span data-stu-id="e80b3-127">Using an encoding object</span></span>](#using-an-encoding-object)

* [<span data-ttu-id="e80b3-128">選擇後援策略</span><span class="sxs-lookup"><span data-stu-id="e80b3-128">Choosing a fallback strategy</span></span>](#choosing-a-fallback-strategy)

* [<span data-ttu-id="e80b3-129">實作自訂後援策略</span><span class="sxs-lookup"><span data-stu-id="e80b3-129">Implementing a custom fallback strategy</span></span>](#implementing-a-custom-fallback-strategy)

## <a name="encodings-in-net"></a><span data-ttu-id="e80b3-130">.NET 中的編碼</span><span class="sxs-lookup"><span data-stu-id="e80b3-130">Encodings in .NET</span></span>

<span data-ttu-id="e80b3-131">.NET 中的所有字元編碼類別都會繼承自 [System.Text.Encoding](xref:System.Text.Encoding) 類別，這是定義所有字元編碼共通功能的抽象類別。</span><span class="sxs-lookup"><span data-stu-id="e80b3-131">All character encoding classes in .NET inherit from the [System.Text.Encoding](xref:System.Text.Encoding) class, which is an abstract class that defines the functionality common to all character encodings.</span></span> <span data-ttu-id="e80b3-132">若要存取 .NET 中實作的個別編碼物件，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e80b3-132">To access the individual encoding objects implemented in .NET, do the following:</span></span>

* <span data-ttu-id="e80b3-133">使用 [Encoding](xref:System.Text.Encoding) 類別的靜態屬性，這些屬性會傳回代表 .NET 中可用之標準字元編碼 (ASCII、UTF-7、UTF-8、UTF-16 和 UTF-32) 的物件。</span><span class="sxs-lookup"><span data-stu-id="e80b3-133">Use the static properties of the [Encoding](xref:System.Text.Encoding) class, which return objects that represent the standard character encodings available in .NET (ASCII, UTF-7, UTF-8, UTF-16, and UTF-32).</span></span> <span data-ttu-id="e80b3-134">例如，[Encoding.Unicode](xref:System.Text.Encoding.Unicode) 屬性會傳回 [UnicodeEncoding](xref:System.Text.UnicodeEncoding) 物件。</span><span class="sxs-lookup"><span data-stu-id="e80b3-134">For example, the [Encoding.Unicode](xref:System.Text.Encoding.Unicode) property returns a [UnicodeEncoding](xref:System.Text.UnicodeEncoding) object.</span></span> <span data-ttu-id="e80b3-135">每個物件會使用取代後援，來處理無法編碼的字串和無法解碼的位元組 </span><span class="sxs-lookup"><span data-stu-id="e80b3-135">Each object uses replacement fallback to handle strings that it cannot encode and bytes that it cannot decode.</span></span> <span data-ttu-id="e80b3-136">(如需詳細資訊，請參閱[取代後援](#replacement-fallback)一節)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-136">(For more information, see the [Replacement fallback](#replacement-fallback) section.)</span></span>

* <span data-ttu-id="e80b3-137">呼叫編碼的類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="e80b3-137">Call the encoding's class constructor.</span></span> <span data-ttu-id="e80b3-138">ASCII、UTF-7、UTF-8、UTF-16 和 UTF-32 編碼的物件可以透過這種方式執行個體化。</span><span class="sxs-lookup"><span data-stu-id="e80b3-138">Objects for the ASCII, UTF-7, UTF-8, UTF-16, and UTF-32 encodings can be instantiated in this way.</span></span> <span data-ttu-id="e80b3-139">每個物件預設會使用取代後援，來處理無法編碼的字串和無法解碼的位元組，不過您可以指定改為擲回例外狀況 </span><span class="sxs-lookup"><span data-stu-id="e80b3-139">By default, each object uses replacement fallback to handle strings that it cannot encode and bytes that it cannot decode, but you can specify that an exception should be thrown instead.</span></span> <span data-ttu-id="e80b3-140">(如需詳細資訊，請參閱[取代後援](#replacement-fallback)及[例外狀況後援](#exception-fallback)兩節)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-140">(For more information, see the [Replacement fallback](#replacement-fallback) and [Exception fallback](#exception-fallback) sections.)</span></span>

* <span data-ttu-id="e80b3-141">呼叫 [Encoding.Encoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) 建構函式，並將代表編碼的整數傳遞給該建構函式。</span><span class="sxs-lookup"><span data-stu-id="e80b3-141">Call the [Encoding.Encoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) constructor and pass it an integer that represents the encoding.</span></span> <span data-ttu-id="e80b3-142">標準編碼物件使用取代後援，來處理無法編碼的字串和無法解碼的位元組，而字碼頁和雙位元組字元集 (DBCS) 編碼物件則是使用自動調整後援 </span><span class="sxs-lookup"><span data-stu-id="e80b3-142">Standard encoding objects use replacement fallback, and code page and double-byte character set (DBCS) encoding objects use best-fit fallback to handle strings that they cannot encode and bytes that they cannot decode.</span></span> <span data-ttu-id="e80b3-143">(如需詳細資訊，請參閱[自動調整後援](#best-fit-fallback)一節)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-143">(For more information, see the [Best-Fit fallback](#best-fit-fallback) section.)</span></span>

* <span data-ttu-id="e80b3-144">呼叫 [Encoding.GetEncoding](xref:System.Text.Encoding.GetEncoding(System.Int32)) 方法，這個方法會傳回 .NET 中可用的任何標準、字碼頁或 DBCS 編碼。</span><span class="sxs-lookup"><span data-stu-id="e80b3-144">Call the [Encoding.GetEncoding](xref:System.Text.Encoding.GetEncoding(System.Int32)) method, which returns any standard, code page, or DBCS encoding available in .NET.</span></span> <span data-ttu-id="e80b3-145">多載可讓您同時為編碼器和解碼器指定後援物件。</span><span class="sxs-lookup"><span data-stu-id="e80b3-145">Overloads let you specify a fallback object for both the encoder and the decoder.</span></span>

> [!NOTE]
> <span data-ttu-id="e80b3-146">Unicode 標準會對每個受支援字集中的每個字元，指派一個字碼指標 (數字) 和一個名稱。</span><span class="sxs-lookup"><span data-stu-id="e80b3-146">The Unicode Standard assigns a code point (a number) and a name to each character in every supported script.</span></span> <span data-ttu-id="e80b3-147">例如，字元 "A" 是由字碼指標 U+0041 和名稱 "LATIN CAPITAL LETTER A" 來表示。</span><span class="sxs-lookup"><span data-stu-id="e80b3-147">For example, the character "A" is represented by the code point U+0041 and the name "LATIN CAPITAL LETTER A".</span></span> <span data-ttu-id="e80b3-148">Unicode 轉換格式 (UTF) 編碼定義將字碼指標編碼為一或多個位元組序列的方式。</span><span class="sxs-lookup"><span data-stu-id="e80b3-148">The Unicode Transformation Format (UTF) encodings define ways to encode that code point into a sequence of one or more bytes.</span></span> <span data-ttu-id="e80b3-149">Unicode 編碼配置簡化全球化應用程式的開發作業，因為它能夠以單一編碼表示任何字元集的字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-149">A Unicode encoding scheme simplifies world-ready application development because it allows characters from any character set to be represented in a single encoding.</span></span> <span data-ttu-id="e80b3-150">應用程式開發人員不再需要追蹤用來產生特定語言或書寫系統字元的編碼配置，同時資料可在各國系統之間共用，而不會損毀。</span><span class="sxs-lookup"><span data-stu-id="e80b3-150">Application developers no longer have to keep track of the encoding scheme that was used to produce characters for a specific language or writing system, and data can be shared among systems internationally without being corrupted.</span></span>
>
>  <span data-ttu-id="e80b3-151">.NET 支援由 Unicode 標準定義的三種編碼：UTF-8、UTF-16 和 UTF-32。</span><span class="sxs-lookup"><span data-stu-id="e80b3-151">.NET supports three encodings defined by the Unicode standard: UTF-8, UTF-16, and UTF-32.</span></span> <span data-ttu-id="e80b3-152">如需詳細資訊，請參閱 [Unicode](http://www.unicode.org/) 首頁的＜Unicode Standard＞。</span><span class="sxs-lookup"><span data-stu-id="e80b3-152">For more information, see The Unicode Standard at the [Unicode](http://www.unicode.org/) home page.</span></span>
 
<span data-ttu-id="e80b3-153">.NET 支援下表所列的字元編碼系統。</span><span class="sxs-lookup"><span data-stu-id="e80b3-153">.NET supports the character encoding systems listed in the following table.</span></span>

<span data-ttu-id="e80b3-154">編碼</span><span class="sxs-lookup"><span data-stu-id="e80b3-154">Encoding</span></span> | <span data-ttu-id="e80b3-155">類別</span><span class="sxs-lookup"><span data-stu-id="e80b3-155">Class</span></span> | <span data-ttu-id="e80b3-156">描述</span><span class="sxs-lookup"><span data-stu-id="e80b3-156">Description</span></span> | <span data-ttu-id="e80b3-157">優點/缺點</span><span class="sxs-lookup"><span data-stu-id="e80b3-157">Advantages/disadvantages</span></span>
-------- | ----- | ----------- | ------------------------ 
<span data-ttu-id="e80b3-158">ASCII</span><span class="sxs-lookup"><span data-stu-id="e80b3-158">ASCII</span></span> | [<span data-ttu-id="e80b3-159">ASCIIEncoding</span><span class="sxs-lookup"><span data-stu-id="e80b3-159">ASCIIEncoding</span></span>](xref:System.Text.ASCIIEncoding) | <span data-ttu-id="e80b3-160">使用位元組較低的七個位元編碼有限範圍的字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-160">Encodes a limited range of characters by using the lower seven bits of a byte.</span></span> | <span data-ttu-id="e80b3-161">由於這個編碼僅支援 U+0000 到 U+007F 之間的字元值，因此大部分的情況下並不適用於國際化的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e80b3-161">Because this encoding only supports character values from U+0000 through U+007F, in most cases it is inadequate for internationalized applications.</span></span>
<span data-ttu-id="e80b3-162">UTF-7</span><span class="sxs-lookup"><span data-stu-id="e80b3-162">UTF-7</span></span> | [<span data-ttu-id="e80b3-163">UTF7Encoding</span><span class="sxs-lookup"><span data-stu-id="e80b3-163">UTF7Encoding</span></span>](xref:System.Text.UTF7Encoding) | <span data-ttu-id="e80b3-164">以 7 位元 ASCII 字元序列表示字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-164">Represents characters as sequences of 7-bit ASCII characters.</span></span> <span data-ttu-id="e80b3-165">非 ASCII 的 Unicode 字元則以 ASCII 字元的逸出序列表示。</span><span class="sxs-lookup"><span data-stu-id="e80b3-165">Non-ASCII Unicode characters are represented by an escape sequence of ASCII characters.</span></span> | <span data-ttu-id="e80b3-166">UTF-7 支援通訊協定，例如電子郵件和新聞群組通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e80b3-166">UTF-7 supports protocols such as e-mail and newsgroup protocols.</span></span> <span data-ttu-id="e80b3-167">不過，UTF-7 並沒有特別安全或穩固。</span><span class="sxs-lookup"><span data-stu-id="e80b3-167">However, UTF-7 is not particularly secure or robust.</span></span> <span data-ttu-id="e80b3-168">在某些情況下，變更一個位元便可能會徹底改變整個 UTF-7 字串的解譯。</span><span class="sxs-lookup"><span data-stu-id="e80b3-168">In some cases, changing one bit can radically alter the interpretation of an entire UTF-7 string.</span></span> <span data-ttu-id="e80b3-169">而在其他情況下，不同的 UTF-7 字串可能會編碼為相同的文字。</span><span class="sxs-lookup"><span data-stu-id="e80b3-169">In other cases, different UTF-7 strings can encode the same text.</span></span> <span data-ttu-id="e80b3-170">對於包含非 ASCII 字元的序列而言，UTF-7 比 UTF-8 需要更多空間，而且編碼/解碼的速度比較慢。</span><span class="sxs-lookup"><span data-stu-id="e80b3-170">For sequences that include non-ASCII characters, UTF-7 requires more space than UTF-8, and encoding/decoding is slower.</span></span> <span data-ttu-id="e80b3-171">因此，您應該盡可能使用 UTF-8，而不是 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="e80b3-171">Consequently, you should use UTF-8 instead of UTF-7 if possible.</span></span>
<span data-ttu-id="e80b3-172">UTF-8</span><span class="sxs-lookup"><span data-stu-id="e80b3-172">UTF-8</span></span> | [<span data-ttu-id="e80b3-173">UTF8Encoding</span><span class="sxs-lookup"><span data-stu-id="e80b3-173">UTF8Encoding</span></span>](xref:System.Text.UTF8Encoding) | <span data-ttu-id="e80b3-174">以一到四個位元組的序列表示每個 Unicode 字碼指標。</span><span class="sxs-lookup"><span data-stu-id="e80b3-174">Represents each Unicode code point as a sequence of one to four bytes.</span></span> | <span data-ttu-id="e80b3-175">UTF-8 支援 8 位元的資料大小，而且適用於許多現有的作業系統。</span><span class="sxs-lookup"><span data-stu-id="e80b3-175">UTF-8 supports 8-bit data sizes and works well with many existing operating systems.</span></span> <span data-ttu-id="e80b3-176">對於 ASCII 字元範圍而言，UTF-8 與 ASCII 編碼完全相同，而且允許範圍更廣的字元集。</span><span class="sxs-lookup"><span data-stu-id="e80b3-176">For the ASCII range of characters, UTF-8 is identical to ASCII encoding and allows a broader set of characters.</span></span> <span data-ttu-id="e80b3-177">不過，針對中日韓 (CJK) 字集，UTF-8 可能要求每個字元需有三個位元組，而且造成的資料大小可能比 UTF-16 還大。</span><span class="sxs-lookup"><span data-stu-id="e80b3-177">However, for Chinese-Japanese-Korean (CJK) scripts, UTF-8 can require three bytes for each character, and can potentially cause larger data sizes than UTF-16.</span></span> <span data-ttu-id="e80b3-178">請注意，ASCII 資料量 (例如 HTML 標記) 有時可能是 CJK 範圍大小增加的原因。</span><span class="sxs-lookup"><span data-stu-id="e80b3-178">Note that sometimes the amount of ASCII data, such as HTML tags, justifies the increased size for the CJK range.</span></span>
<span data-ttu-id="e80b3-179">UTF-16</span><span class="sxs-lookup"><span data-stu-id="e80b3-179">UTF-16</span></span> | [<span data-ttu-id="e80b3-180">UnicodeEncoding</span><span class="sxs-lookup"><span data-stu-id="e80b3-180">UnicodeEncoding</span></span>](xref:System.Text.UnicodeEncoding) | <span data-ttu-id="e80b3-181">以一個或兩個 16 位元整數的序列表示每個 Unicode 字碼指標。</span><span class="sxs-lookup"><span data-stu-id="e80b3-181">Represents each Unicode code point as a sequence of one or two 16-bit integers.</span></span> <span data-ttu-id="e80b3-182">雖然 Unicode 補充字元 (U+10000 及以上) 需要兩個 UTF-16 Surrogate 字碼指標，但最常用的 Unicode 字元只需要一個 UTF-16 字碼指標。</span><span class="sxs-lookup"><span data-stu-id="e80b3-182">Most common Unicode characters require only one UTF-16 code point, although Unicode supplementary characters (U+10000 and greater) require two UTF-16 surrogate code points.</span></span> <span data-ttu-id="e80b3-183">同時支援位元組由小到大和位元組由大到小的位元組順序。</span><span class="sxs-lookup"><span data-stu-id="e80b3-183">Both little-endian and big-endian byte orders are supported.</span></span> | <span data-ttu-id="e80b3-184">Common Language Runtime 會使用 UTF-16 編碼表示 Char 和 String 值，而 Windows 作業系統會使用該編碼表示 WCHAR 值。</span><span class="sxs-lookup"><span data-stu-id="e80b3-184">UTF-16 encoding is used by the common language runtime to represent Char and String values, and it is used by the Windows operating system to represent WCHAR values.</span></span>
<span data-ttu-id="e80b3-185">UTF-32</span><span class="sxs-lookup"><span data-stu-id="e80b3-185">UTF-32</span></span> | [<span data-ttu-id="e80b3-186">UTF32Encoding</span><span class="sxs-lookup"><span data-stu-id="e80b3-186">UTF32Encoding</span></span>](xref:System.Text.UTF32Encoding) | <span data-ttu-id="e80b3-187">以 32 位元整數表示每個 Unicode 字碼指標。</span><span class="sxs-lookup"><span data-stu-id="e80b3-187">Represents each Unicode code point as a 32-bit integer.</span></span> <span data-ttu-id="e80b3-188">同時支援位元組由小到大和位元組由大到小的位元組順序。</span><span class="sxs-lookup"><span data-stu-id="e80b3-188">Both little-endian and big-endian byte orders are supported.</span></span> | <span data-ttu-id="e80b3-189">當編碼空間對作業系統十分重要，而應用程式想要在作業系統上避免 UTF-16 編碼的 Surrogate 字碼指標行為時，可以使用 UTF-32 編碼。</span><span class="sxs-lookup"><span data-stu-id="e80b3-189">UTF-32 encoding is used when applications want to avoid the surrogate code point behavior of UTF-16 encoding on operating systems for which encoded space is too important.</span></span> <span data-ttu-id="e80b3-190">畫面上呈現的單一字符仍然可以使用一個以上的 UTF-32 字元編碼。</span><span class="sxs-lookup"><span data-stu-id="e80b3-190">Single glyphs rendered on a display can still be encoded with more than one UTF-32 character.</span></span>

<span data-ttu-id="e80b3-191">這些編碼可讓您處理 Unicode 字元，以及舊版應用程式中最常用的編碼。</span><span class="sxs-lookup"><span data-stu-id="e80b3-191">These encodings enable you to work with Unicode characters as well as with encodings that are most commonly used in legacy applications.</span></span> <span data-ttu-id="e80b3-192">此外，您可以藉由定義衍生自 [Encoding](xref:System.Text.Encoding) 的類別及覆寫其成員，來建立自訂編碼。</span><span class="sxs-lookup"><span data-stu-id="e80b3-192">In addition, you can create a custom encoding by defining a class that derives from [Encoding](xref:System.Text.Encoding) and overriding its members.</span></span>

> [!NOTE]
> <span data-ttu-id="e80b3-193">根據預設，除了字碼頁 28591 以及UTF-8 和 UTF-16 等 Unicode 編碼之外，.NET Core 不會提供任何字碼頁編碼。</span><span class="sxs-lookup"><span data-stu-id="e80b3-193">By default, .NET Core does not make available any code page encodings other than code page 28591 and the Unicode encodings, such as UTF-8 and UTF-16.</span></span> <span data-ttu-id="e80b3-194">不過，您可以將在以 .NET Framework 為目標的標準 Windows 應用程式中找到的字碼頁編碼，加入您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e80b3-194">However, you can add the code page encodings found in standard Windows apps that target the .NET Framework to your app.</span></span> <span data-ttu-id="e80b3-195">如需完整資訊，請參閱 [EncodingProvider](xref:System.Text.EncodingProvider) 主題。</span><span class="sxs-lookup"><span data-stu-id="e80b3-195">For complete information, see the [EncodingProvider](xref:System.Text.EncodingProvider) topic.</span></span> 

## <a name="selecting-an-encoding-class"></a><span data-ttu-id="e80b3-196">選取編碼類別</span><span class="sxs-lookup"><span data-stu-id="e80b3-196">Selecting an Encoding class</span></span>

<span data-ttu-id="e80b3-197">如果您有機會選擇應用程式使用的編碼，則應該使用 Unicode 編碼，最好是 [UTF8Encoding](xref:System.Text.UTF8Encoding) 或 [UnicodeEncoding](xref:System.Text.UnicodeEncoding)</span><span class="sxs-lookup"><span data-stu-id="e80b3-197">If you have the opportunity to choose the encoding to be used by your application, you should use a Unicode encoding, preferably either [UTF8Encoding](xref:System.Text.UTF8Encoding) or [UnicodeEncoding](xref:System.Text.UnicodeEncoding).</span></span> <span data-ttu-id="e80b3-198">(.NET 也支援第三種 Unicode 編碼 [UTF32Encoding](xref:System.Text.UTF32Encoding))。</span><span class="sxs-lookup"><span data-stu-id="e80b3-198">(.NET also supports a third Unicode encoding, [UTF32Encoding](xref:System.Text.UTF32Encoding).)</span></span> 

<span data-ttu-id="e80b3-199">如果您打算使用 ASCII 編碼 ([ASCIIEncoding](xref:System.Text.ASCIIEncoding))，請改為選擇 [UTF8Encoding](xref:System.Text.UTF8Encoding)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-199">If you are planning to use an ASCII encoding ([ASCIIEncoding](xref:System.Text.ASCIIEncoding)), choose [UTF8Encoding](xref:System.Text.UTF8Encoding) instead.</span></span> <span data-ttu-id="e80b3-200">這兩種編碼對於 ASCII 字元集而言完全相同，但是 [UTF8Encoding](xref:System.Text.UTF8Encoding) 具有下列優點：</span><span class="sxs-lookup"><span data-stu-id="e80b3-200">The two encodings are identical for the ASCII character set, but [UTF8Encoding](xref:System.Text.UTF8Encoding) has the following advantages:</span></span> 

* <span data-ttu-id="e80b3-201">它可以表示每個 Unicode 字元，而 [ASCIIEncoding](xref:System.Text.ASCIIEncoding) 只支援 U+0000 與 U+007F 之間的 Unicode 字元值。</span><span class="sxs-lookup"><span data-stu-id="e80b3-201">It can represent every Unicode character, whereas [ASCIIEncoding](xref:System.Text.ASCIIEncoding) supports only the Unicode character values between U+0000 and U+007F.</span></span>

* <span data-ttu-id="e80b3-202">它提供錯誤偵測且具有較佳的安全性。</span><span class="sxs-lookup"><span data-stu-id="e80b3-202">It provides error detection and better security.</span></span>

* <span data-ttu-id="e80b3-203">它已調整成其可能的最快速度，因此在速度上應該會超過其他任何編碼。</span><span class="sxs-lookup"><span data-stu-id="e80b3-203">It has been tuned to be as fast as possible and should be faster than any other encoding.</span></span> <span data-ttu-id="e80b3-204">即使為全部都是 ASCII 的內容，使用 [UTF8Encoding](xref:System.Text.UTF8Encoding) 執行的作業也會快過使用 [ASCIIEncoding](xref:System.Text.ASCIIEncoding) 執行的作業。</span><span class="sxs-lookup"><span data-stu-id="e80b3-204">Even for content that is entirely ASCII, operations performed with [UTF8Encoding](xref:System.Text.UTF8Encoding) are faster than operations performed with [ASCIIEncoding](xref:System.Text.ASCIIEncoding).</span></span>

<span data-ttu-id="e80b3-205">您應該考慮只對舊版應用程式使用 [ASCIIEncoding](xref:System.Text.ASCIIEncoding)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-205">You should consider using [ASCIIEncoding](xref:System.Text.ASCIIEncoding) only for legacy applications.</span></span> <span data-ttu-id="e80b3-206">不過，即使是舊版應用程式，[UTF8Encoding](xref:System.Text.UTF8Encoding) 仍然可能是較佳的選擇，原因如下 (假設使用預設值)：</span><span class="sxs-lookup"><span data-stu-id="e80b3-206">However, even for legacy applications, [UTF8Encoding](xref:System.Text.UTF8Encoding) might be a better choice for the following reasons (assuming default settings):</span></span>

* <span data-ttu-id="e80b3-207">如果您的應用程式具有的內容不完全是 ASCII，而且使用 [ASCIIEncoding](xref:System.Text.ASCIIEncoding) 編碼該內容，則每個非 ASCII 字元都會編碼為問號 (?)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-207">If your application has content that is not strictly ASCII and encodes it with [ASCIIEncoding](xref:System.Text.ASCIIEncoding), each non-ASCII character encodes as a question mark (?).</span></span> <span data-ttu-id="e80b3-208">如果應用程式接著解碼這份資料，資訊就會遺失。</span><span class="sxs-lookup"><span data-stu-id="e80b3-208">If the application then decodes this data, the information is lost.</span></span>


* <span data-ttu-id="e80b3-209">如果應用程式具有的內容不完全是 ASCII，而且使用 [UTF8Encoding](xref:System.Text.UTF8Encoding) 編碼該內容，將結果解譯為 ASCII 會難以理解。</span><span class="sxs-lookup"><span data-stu-id="e80b3-209">If your application has content that is not strictly ASCII and encodes it with [UTF8Encoding](xref:System.Text.UTF8Encoding), the result seems unintelligible if interpreted as ASCII.</span></span> <span data-ttu-id="e80b3-210">不過，如果應用程式接著使用 UTF-8 解碼器來解碼這份資料，則該資料會成功地執行來回轉換。</span><span class="sxs-lookup"><span data-stu-id="e80b3-210">However, if the application then uses a UTF-8 decoder to decode this data, the data performs a round trip successfully.</span></span>

<span data-ttu-id="e80b3-211">在 Web 應用程式中，傳送至用戶端以回應 Web 要求的字元應該反映用戶端上使用的編碼。</span><span class="sxs-lookup"><span data-stu-id="e80b3-211">In a web application, characters sent to the client in response to a web request should reflect the encoding used on the client.</span></span> <span data-ttu-id="e80b3-212">在大部分情況下，您應該將 [HttpResponse.ContentEncoding](xref:System.Net.HttpResponseHeader.ContentEncoding) 屬性設定為 [HttpRequestHeader.ContentEncoding](xref:System.Net.HttpRequestHeader.ContentEncoding) 屬性所傳回的值，以便以使用者預期的編碼來顯示文字。</span><span class="sxs-lookup"><span data-stu-id="e80b3-212">In most cases, you should set the [HttpResponse.ContentEncoding](xref:System.Net.HttpResponseHeader.ContentEncoding) property to the value returned by the [HttpRequestHeader.ContentEncoding](xref:System.Net.HttpRequestHeader.ContentEncoding) property to display text in the encoding that the user expects.</span></span>

## <a name="using-an-encoding-object"></a><span data-ttu-id="e80b3-213">使用編碼物件</span><span class="sxs-lookup"><span data-stu-id="e80b3-213">Using an encoding object</span></span>

<span data-ttu-id="e80b3-214">編碼器會將字元字串 (最常見為 Unicode 字元) 轉換成其對等數值 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-214">An encoder converts a string of characters (most commonly, Unicode characters) to its numeric (byte) equivalent.</span></span> <span data-ttu-id="e80b3-215">例如，您可能使用 ASCII 編碼器將 Unicode 字元轉換成 ASCII，以便在主控台上顯示。</span><span class="sxs-lookup"><span data-stu-id="e80b3-215">For example, you might use an ASCII encoder to convert Unicode characters to ASCII so that they can be displayed at the console.</span></span> <span data-ttu-id="e80b3-216">若要執行轉換，請呼叫 [Encoding.GetBytes](xref:System.Text.Encoding.GetBytes(System.Char[])) 方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-216">To perform the conversion, you call the [Encoding.GetBytes](xref:System.Text.Encoding.GetBytes(System.Char[])) method.</span></span> <span data-ttu-id="e80b3-217">如果您想要在執行編碼之前判斷儲存編碼的字元需要多少個位元組，可以呼叫 [GetByteCount](xref:System.Text.Encoding.GetByteCount(System.Char[])) 方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-217">If you want to determine how many bytes are needed to store the encoded characters before performing the encoding, you can call the [GetByteCount](xref:System.Text.Encoding.GetByteCount(System.Char[])) method.</span></span>

<span data-ttu-id="e80b3-218">下列範例會在兩項不同的作業中使用單一位元組陣列編碼字串。</span><span class="sxs-lookup"><span data-stu-id="e80b3-218">The following example uses a single byte array to encode strings in two separate operations.</span></span> <span data-ttu-id="e80b3-219">它會保留一個索引，指出下一組 ASCII 編碼位元組在位元組陣列中的開始位置。</span><span class="sxs-lookup"><span data-stu-id="e80b3-219">It maintains an index that indicates the starting position in the byte array for the next set of ASCII-encoded bytes.</span></span> <span data-ttu-id="e80b3-220">它會呼叫 [ASCIIEncoding.GetByteCount(String)](xref:System.Text.ASCIIEncoding.GetByteCount(System.String)) 方法，確保位元組陣列的大小夠大，足以容納編碼的字串。</span><span class="sxs-lookup"><span data-stu-id="e80b3-220">It calls the [ASCIIEncoding.GetByteCount(String)](xref:System.Text.ASCIIEncoding.GetByteCount(System.String)) method to ensure that the byte array is large enough to accommodate the encoded string.</span></span> <span data-ttu-id="e80b3-221">然後它會呼叫 [ASCIIEncoding.GetBytes(String, Int32, Int32, Byte[], Int32)](xref:System.Text.ASCIIEncoding.GetBytes(System.Char[],System.Int32,System.Int32,System.Byte[],System.Int32)) 方法來編碼字串中的字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-221">It then calls the [ASCIIEncoding.GetBytes(String, Int32, Int32, Byte[], Int32)](xref:System.Text.ASCIIEncoding.GetBytes(System.Char[],System.Int32,System.Int32,System.Byte[],System.Int32)) method to encode the characters in the string.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings= { "This is the first sentence. ", 
                          "This is the second sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;

      // Create array of adequate size.
      byte[] bytes = new byte[49];
      // Create index for current position of array.
      int index = 0;

      Console.WriteLine("Strings to encode:");
      foreach (var stringValue in strings) {
         Console.WriteLine("   {0}", stringValue);

         int count = asciiEncoding.GetByteCount(stringValue);
         if (count + index >=  bytes.Length)
            Array.Resize(ref bytes, bytes.Length + 50);

         int written = asciiEncoding.GetBytes(stringValue, 0, 
                                              stringValue.Length, 
                                              bytes, index);    

         index = index + written; 
      } 
      Console.WriteLine("\nEncoded bytes:");
      Console.WriteLine("{0}", ShowByteValues(bytes, index));
      Console.WriteLine();

      // Decode Unicode byte array to a string.
      string newString = asciiEncoding.GetString(bytes, 0, index);
      Console.WriteLine("Decoded: {0}", newString);
   }

   private static string ShowByteValues(byte[] bytes, int last ) 
   {
      string returnString = "   ";
      for (int ctr = 0; ctr <= last - 1; ctr++) {
         if (ctr % 20 == 0)
            returnString += "\n   ";
         returnString += String.Format("{0:X2} ", bytes[ctr]);
      }
      return returnString;
   }
}
// The example displays the following output:
//       Strings to encode:
//          This is the first sentence.
//          This is the second sentence.
//       
//       Encoded bytes:
//       
//          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
//          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
//       
//       Decoded: This is the first sentence. This is the second sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII

      ' Create array of adequate size.
      Dim bytes(50) As Byte
      ' Create index for current position of array.
      Dim index As Integer = 0

      Console.WriteLine("Strings to encode:")
      For Each stringValue In strings
         Console.WriteLine("   {0}", stringValue)

         Dim count As Integer = asciiEncoding.GetByteCount(stringValue)
         If count + index >=  bytes.Length Then
            Array.Resize(bytes, bytes.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetBytes(stringValue, 0, 
                                                         stringValue.Length, 
                                                         bytes, index)    

         index = index + written 
      Next 
      Console.WriteLine()
      Console.WriteLine("Encoded bytes:")
      Console.WriteLine("{0}", ShowByteValues(bytes, index))
      Console.WriteLine()

      ' Decode Unicode byte array to a string.
      Dim newString As String = asciiEncoding.GetString(bytes, 0, index)
      Console.WriteLine("Decoded: {0}", newString)
   End Sub

   Private Function ShowByteValues(bytes As Byte(), last As Integer) As String
      Dim returnString As String = "   "
      For ctr As Integer = 0 To last - 1
         If ctr Mod 20 = 0 Then returnString += vbCrLf + "   "
         returnString += String.Format("{0:X2} ", bytes(ctr))
      Next
      Return returnString
   End Function
End Module
' The example displays the following output:
'       Strings to encode:
'          This is the first sentence.
'          This is the second sentence.
'       
'       Encoded bytes:
'       
'          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
'          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
'       
'       Decoded: This is the first sentence. This is the second sentence.
```

<span data-ttu-id="e80b3-222">解碼器會將反映特定字元編碼的位元組陣列轉換成字元陣列或字串中的字元集。</span><span class="sxs-lookup"><span data-stu-id="e80b3-222">A decoder converts a byte array that reflects a particular character encoding into a set of characters, either in a character array or in a string.</span></span> <span data-ttu-id="e80b3-223">若要將位元組陣列解碼為字元陣列，請呼叫 [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) 方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-223">To decode a byte array into a character array, you call the [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) method.</span></span> <span data-ttu-id="e80b3-224">若要將位元組陣列解碼為字串，請呼叫 [GetString](xref:System.Text.Encoding.GetString(System.Byte[])) 方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-224">To decode a byte array into a string, you call the [GetString](xref:System.Text.Encoding.GetString(System.Byte[])) method.</span></span> <span data-ttu-id="e80b3-225">如果您想要在執行解碼之前判斷儲存解碼的位元組需要多少個字元，可以呼叫 [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) 方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-225">If you want to determine how many characters are needed to store the decoded bytes before performing the decoding, you can call the [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) method.</span></span>

<span data-ttu-id="e80b3-226">下列範例會編碼三個字串，然後將這些字串解碼為單一字元陣列。</span><span class="sxs-lookup"><span data-stu-id="e80b3-226">The following example encodes three strings and then decodes them into a single array of characters.</span></span> <span data-ttu-id="e80b3-227">它會保留一個索引，指出下一組解碼的字元在字元陣列中的開始位置。</span><span class="sxs-lookup"><span data-stu-id="e80b3-227">It maintains an index that indicates the starting position in the character array for the next set of decoded characters.</span></span> <span data-ttu-id="e80b3-228">它會呼叫 [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) 方法，確保字元陣列的大小夠大，足以容納所有解碼的字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-228">It calls the [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) method to ensure that the character array is large enough to accommodate all the decoded characters.</span></span> <span data-ttu-id="e80b3-229">然後它會呼叫 [ASCIIEncoding.GetChars(Byte[], Int32, Int32, Char[], Int32)](xref:System.Text.ASCIIEncoding.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) 方法來解碼位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="e80b3-229">It then calls the [ASCIIEncoding.GetChars(Byte[], Int32, Int32, Char[], Int32)](xref:System.Text.ASCIIEncoding.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) method to decode the byte array.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings = { "This is the first sentence. ", 
                           "This is the second sentence. ",
                           "This is the third sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;
      // Array to hold encoded bytes.
      byte[] bytes;
      // Array to hold decoded characters.
      char[] chars = new char[50];
      // Create index for current position of character array.
      int index = 0;     

      foreach (var stringValue in strings) {
         Console.WriteLine("String to Encode: {0}", stringValue);
         // Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue);
         // Display the encoded bytes.
         Console.Write("Encoded bytes: ");
         for (int ctr = 0; ctr < bytes.Length; ctr++)
            Console.Write(" {0}{1:X2}", 
                          ctr % 20 == 0 ? Environment.NewLine : "", 
                          bytes[ctr]);
         Console.WriteLine();

         // Decode the bytes to a single character array.
         int count = asciiEncoding.GetCharCount(bytes);
         if (count + index >=  chars.Length)
            Array.Resize(ref chars, chars.Length + 50);

         int written = asciiEncoding.GetChars(bytes, 0, 
                                              bytes.Length, 
                                              chars, index);              
         index = index + written;
         Console.WriteLine();       
      }

      // Instantiate a single string containing the characters.
      string decodedString = new string(chars, 0, index - 1);
      Console.WriteLine("Decoded string: ");
      Console.WriteLine(decodedString);
   }
}
// The example displays the following output:
//    String to Encode: This is the first sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the second sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
//    65 6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the third sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    Decoded string:
//    This is the first sentence. This is the second sentence. This is the third sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. ",
                                  "This is the third sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII
      ' Array to hold encoded bytes.
      Dim bytes() As Byte
      ' Array to hold decoded characters.
      Dim chars(50) As Char
      ' Create index for current position of character array.
      Dim index As Integer     

      For Each stringValue In strings
         Console.WriteLine("String to Encode: {0}", stringValue)
         ' Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue)
         ' Display the encoded bytes.
         Console.Write("Encoded bytes: ")
         For ctr As Integer = 0 To bytes.Length - 1
            Console.Write(" {0}{1:X2}", If(ctr Mod 20 = 0, vbCrLf, ""), 
                                        bytes(ctr))
         Next         
         Console.WriteLine()

         ' Decode the bytes to a single character array.
         Dim count As Integer = asciiEncoding.GetCharCount(bytes)
         If count + index >=  chars.Length Then
            Array.Resize(chars, chars.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetChars(bytes, 0, 
                                                         bytes.Length, 
                                                         chars, index)              
         index = index + written
         Console.WriteLine()       
      Next

      ' Instantiate a single string containing the characters.
      Dim decodedString As New String(chars, 0, index - 1)
      Console.WriteLine("Decoded string: ")
      Console.WriteLine(decodedString)
   End Sub
End Module
' The example displays the following output:
'    String to Encode: This is the first sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the second sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
'    65 6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the third sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    Decoded string:
'    This is the first sentence. This is the second sentence. This is the third sentence.
```

<span data-ttu-id="e80b3-230">衍生自 [Encoding](xref:System.Text.Encoding) 之類別的編碼和解碼方法設計成可處理一組完整的資料；也就是說，單一方法呼叫中會提供所有要編碼或解碼的資料。</span><span class="sxs-lookup"><span data-stu-id="e80b3-230">The encoding and decoding methods of a class derived from [Encoding](xref:System.Text.Encoding) are designed to work on a complete set of data; that is, all the data to be encoded or decoded is supplied in a single method call.</span></span> <span data-ttu-id="e80b3-231">不過，在某些情況下，資料是以資料流提供，因此只能從個別讀取作業取得要編碼或解碼的資料。</span><span class="sxs-lookup"><span data-stu-id="e80b3-231">However, in some cases, data is available in a stream, and the data to be encoded or decoded may be available only from separate read operations.</span></span> <span data-ttu-id="e80b3-232">因此，編碼或解碼作業必須記住之前叫用時的任何儲存狀態。</span><span class="sxs-lookup"><span data-stu-id="e80b3-232">This requires the encoding or decoding operation to remember any saved state from its previous invocation.</span></span> <span data-ttu-id="e80b3-233">衍生自 [Encoder](xref:System.Text.Encoder) 和 [Decoder](xref:System.Text.Decoder) 之類別的方法能夠處理橫跨多個方法呼叫的編碼和解碼作業。</span><span class="sxs-lookup"><span data-stu-id="e80b3-233">Methods of classes derived from [Encoder](xref:System.Text.Encoder) and [Decoder](xref:System.Text.Decoder) are able to handle encoding and decoding operations that span multiple method calls.</span></span>

<span data-ttu-id="e80b3-234">特定編碼的 [Encoder](xref:System.Text.Encoder) 物件可從該編碼的 [Encoding.GetEncoder](xref:System.Text.Encoding.GetEncoder) 屬性取得。</span><span class="sxs-lookup"><span data-stu-id="e80b3-234">An [Encoder](xref:System.Text.Encoder) object for a particular encoding is available from that encoding's [Encoding.GetEncoder](xref:System.Text.Encoding.GetEncoder) property.</span></span> <span data-ttu-id="e80b3-235">特定編碼的 [Decoder](xref:System.Text.Decoder) 物件可從該編碼的 [Encoding.GetDecoder](xref:System.Text.Encoding.GetDecoder) 屬性取得。</span><span class="sxs-lookup"><span data-stu-id="e80b3-235">A [Decoder](xref:System.Text.Decoder) object for a particular encoding is available from that encoding's [Encoding.GetDecoder](xref:System.Text.Encoding.GetDecoder) property.</span></span> <span data-ttu-id="e80b3-236">若為解碼作業，請注意衍生自 [Decoder](xref:System.Text.Decoder) 的類別包含 [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) 方法，但是沒有對應至 [Encoding.GetString](xref:System.Text.Encoding.GetString(System.Byte[])) 的方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-236">For decoding operations, note that classes derived from [Decoder](xref:System.Text.Decoder) include a [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) method, but they do not have a method that corresponds to [Encoding.GetString](xref:System.Text.Encoding.GetString(System.Byte[])).</span></span>

<span data-ttu-id="e80b3-237">下列範例說明使用 [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) 和 [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) 方法解碼 Unicode 位元組陣列的差異。</span><span class="sxs-lookup"><span data-stu-id="e80b3-237">The following example illustrates the difference between using the [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) and [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) methods for decoding a Unicode byte array.</span></span> <span data-ttu-id="e80b3-238">這個範例會將包含某些 Unicode 字元的字串編碼為檔案，然後使用這兩種解碼方法進行解碼，且一次解碼十個位元組。</span><span class="sxs-lookup"><span data-stu-id="e80b3-238">The example encodes a string that contains some Unicode characters to a file, and then uses the two decoding methods to decode them ten bytes at a time.</span></span> <span data-ttu-id="e80b3-239">由於 Surrogate 字組會在第十個和第十一個位元組發生，因此會在不同的方法呼叫中另外解碼。</span><span class="sxs-lookup"><span data-stu-id="e80b3-239">Because a surrogate pair occurs in the tenth and eleventh bytes, it is decoded in separate method calls.</span></span> <span data-ttu-id="e80b3-240">如輸出所示，[Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) 方法無法正確解碼位元組，而是將它們取代為 U+FFFD (REPLACEMENT CHARACTER)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-240">As the output shows, the [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) method is not able to correctly decode the bytes and instead replaces them with U+FFFD (REPLACEMENT CHARACTER).</span></span> <span data-ttu-id="e80b3-241">另一方面，[Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) 方法能夠成功解碼位元組陣列並取得原始字串。</span><span class="sxs-lookup"><span data-stu-id="e80b3-241">On the other hand, the [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) method is able to successfully decode the byte array to get the original string.</span></span>

```csharp
using System;
using System.IO;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Use default replacement fallback for invalid encoding.
      UnicodeEncoding enc = new UnicodeEncoding(true, false, false);

      // Define a string with various Unicode characters.
      string str1 = "AB YZ 19 \uD800\udc05 \u00e4"; 
      str1 += "Unicode characters. \u00a9 \u010C s \u0062\u0308"; 
      Console.WriteLine("Created original string...\n");

      // Convert string to byte array.                     
      byte[] bytes = enc.GetBytes(str1);

      FileStream fs = File.Create(@".\characters.bin");
      BinaryWriter bw = new BinaryWriter(fs);
      bw.Write(bytes);
      bw.Close();

      // Read bytes from file.
      FileStream fsIn = File.OpenRead(@".\characters.bin");
      BinaryReader br = new BinaryReader(fsIn);

      const int count = 10;            // Number of bytes to read at a time. 
      byte[] bytesRead = new byte[10]; // Buffer (byte array).
      int read;                        // Number of bytes actually read. 
      string str2 = String.Empty;      // Decoded string.

      // Try using Encoding object for all operations.
      do { 
         read = br.Read(bytesRead, 0, count);
         str2 += enc.GetString(bytesRead, 0, read); 
      } while (read == count);
      br.Close();
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...");
      CompareForEquality(str1, str2);
      Console.WriteLine();

      // Use Decoder for all operations.
      fsIn = File.OpenRead(@".\characters.bin");
      br = new BinaryReader(fsIn);
      Decoder decoder = enc.GetDecoder();
      char[] chars = new char[50];
      int index = 0;                   // Next character to write in array.
      int written = 0;                 // Number of chars written to array.
      do { 
         read = br.Read(bytesRead, 0, count);
         if (index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length) 
            Array.Resize(ref chars, chars.Length + 50);

         written = decoder.GetChars(bytesRead, 0, read, chars, index);
         index += written;                          
      } while (read == count);
      br.Close();            
      // Instantiate a string with the decoded characters.
      string str3 = new String(chars, 0, index); 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...");
      CompareForEquality(str1, str3); 
   }

   private static void CompareForEquality(string original, string decoded)
   {
      bool result = original.Equals(decoded);
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal));
      if (! result) {
         Console.WriteLine("Code points in original string:");
         foreach (var ch in original)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();

         Console.WriteLine("Code points in decoded string:");
         foreach (var ch in decoded)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    Created original string...
//    
//    Decoded string using UnicodeEncoding.GetString()...
//    original = decoded: False
//    Code points in original string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    Code points in decoded string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    
//    Decoded string using UnicodeEncoding.Decoder.GetString()...
//    original = decoded: True
```

```vb
Imports System.IO
Imports System.Text

Module Example
   Public Sub Main()
      ' Use default replacement fallback for invalid encoding.
      Dim enc As New UnicodeEncoding(True, False, False)

      ' Define a string with various Unicode characters.
      Dim str1 As String = String.Format("AB YZ 19 {0}{1} {2}", 
                                         ChrW(&hD800), ChrW(&hDC05), ChrW(&h00e4))
      str1 += String.Format("Unicode characters. {0} {1} s {2}{3}", 
                            ChrW(&h00a9), ChrW(&h010C), ChrW(&h0062), ChrW(&h0308))
      Console.WriteLine("Created original string...")
      Console.WriteLine()

      ' Convert string to byte array.                     
      Dim bytes() As Byte = enc.GetBytes(str1)

      Dim fs As FileStream = File.Create(".\characters.bin")
      Dim bw As New BinaryWriter(fs)
      bw.Write(bytes)
      bw.Close()

      ' Read bytes from file.
      Dim fsIn As FileStream = File.OpenRead(".\characters.bin")
      Dim br As New BinaryReader(fsIn)

      Const count As Integer = 10      ' Number of bytes to read at a time. 
      Dim bytesRead(9) As Byte         ' Buffer (byte array).
      Dim read As Integer              ' Number of bytes actually read. 
      Dim str2 As String = ""          ' Decoded string.

      ' Try using Encoding object for all operations.
      Do 
         read = br.Read(bytesRead, 0, count)
         str2 += enc.GetString(bytesRead, 0, read) 
      Loop While read = count
      br.Close()
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...")
      CompareForEquality(str1, str2)
      Console.WriteLine()

      ' Use Decoder for all operations.
      fsIn = File.OpenRead(".\characters.bin")
      br = New BinaryReader(fsIn)
      Dim decoder As Decoder = enc.GetDecoder()
      Dim chars(50) As Char
      Dim index As Integer = 0         ' Next character to write in array.
      Dim written As Integer = 0       ' Number of chars written to array.
      Do 
         read = br.Read(bytesRead, 0, count)
         If index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length Then 
            Array.Resize(chars, chars.Length + 50)
         End If   
         written = decoder.GetChars(bytesRead, 0, read, chars, index)
         index += written                          
      Loop While read = count
      br.Close()            
      ' Instantiate a string with the decoded characters.
      Dim str3 As New String(chars, 0, index) 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...")
      CompareForEquality(str1, str3) 
   End Sub

   Private Sub CompareForEquality(original As String, decoded As String)
      Dim result As Boolean = original.Equals(decoded)
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal))
      If Not result Then
         Console.WriteLine("Code points in original string:")
         For Each ch In original
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()

         Console.WriteLine("Code points in decoded string:")
         For Each ch In decoded
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
' The example displays the following output:
'    Created original string...
'    
'    Decoded string using UnicodeEncoding.GetString()...
'    original = decoded: False
'    Code points in original string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    Code points in decoded string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    
'    Decoded string using UnicodeEncoding.Decoder.GetString()...
'    original = decoded: True
```

## <a name="choosing-a-fallback-strategy"></a><span data-ttu-id="e80b3-242">選擇後援策略</span><span class="sxs-lookup"><span data-stu-id="e80b3-242">Choosing a fallback strategy</span></span>

<span data-ttu-id="e80b3-243">當某個方法嘗試編碼或解碼字元，但是沒有任何對應存在時，它就必須實作後援策略，以決定應該如何處理失敗的對應。</span><span class="sxs-lookup"><span data-stu-id="e80b3-243">When a method tries to encode or decode a character but no mapping exists, it must implement a fallback strategy that determines how the failed mapping should be handled.</span></span> <span data-ttu-id="e80b3-244">後援策略有三種類型：</span><span class="sxs-lookup"><span data-stu-id="e80b3-244">There are three types of fallback strategies:</span></span> 

* <span data-ttu-id="e80b3-245">自動調整後援</span><span class="sxs-lookup"><span data-stu-id="e80b3-245">Best-fit fallback</span></span>

* <span data-ttu-id="e80b3-246">取代後援</span><span class="sxs-lookup"><span data-stu-id="e80b3-246">Replacement fallback</span></span>

* <span data-ttu-id="e80b3-247">例外狀況後援</span><span class="sxs-lookup"><span data-stu-id="e80b3-247">Exception fallback</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e80b3-248">編碼作業最常在 Unicode 字元無法對應至特定字碼頁編碼時發生問題。</span><span class="sxs-lookup"><span data-stu-id="e80b3-248">The most common problems in encoding operations occur when a Unicode character cannot be mapped to a particular code page encoding.</span></span> <span data-ttu-id="e80b3-249">解碼作業最常在無效的位元組序列無法轉譯為有效的 Unicode 字元時發生問題。</span><span class="sxs-lookup"><span data-stu-id="e80b3-249">The most common problems in decoding operations occur when invalid byte sequences cannot be translated into valid Unicode characters.</span></span> <span data-ttu-id="e80b3-250">因此，您應該知道特定編碼物件所使用的後援策略。</span><span class="sxs-lookup"><span data-stu-id="e80b3-250">For these reasons, you should know which fallback strategy a particular encoding object uses.</span></span> <span data-ttu-id="e80b3-251">您應該在執行個體化編碼物件時，盡可能指定該物件所使用的後援策略。</span><span class="sxs-lookup"><span data-stu-id="e80b3-251">Whenever possible, you should specify the fallback strategy used by an encoding object when you instantiate the object.</span></span>
 
### <a name="best-fit-fallback"></a><span data-ttu-id="e80b3-252">自動調整後援</span><span class="sxs-lookup"><span data-stu-id="e80b3-252">Best-fit fallback</span></span>

<span data-ttu-id="e80b3-253">當字元在目標編碼中沒有完全相符的字元時，編碼器可以嘗試將該字元對應至類似的字元</span><span class="sxs-lookup"><span data-stu-id="e80b3-253">When a character does not have an exact match in the target encoding, the encoder can try to map it to a similar character.</span></span> <span data-ttu-id="e80b3-254">(自動調整後援大部分是針對編碼問題，而不是針對解碼問題。</span><span class="sxs-lookup"><span data-stu-id="e80b3-254">(Best-fit fallback is mostly an encoding rather than a decoding issue.</span></span> <span data-ttu-id="e80b3-255">很少有字碼頁包含無法成功對應至 Unicode 的字元)。自動調整後援是 [Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) 和 [Encoding.GetEncoding(String)](xref:System.Text.Encoding.GetEncoding(System.String)) 多載所擷取之字碼頁和雙位元組字元集編碼的預設值。</span><span class="sxs-lookup"><span data-stu-id="e80b3-255">There are very few code pages that contain characters that cannot be successfully mapped to Unicode.) Best-fit fallback is the default for code page and double-byte character set encodings that are retrieved by the [Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) and [Encoding.GetEncoding(String)](xref:System.Text.Encoding.GetEncoding(System.String)) overloads.</span></span>

> [!NOTE]
> <span data-ttu-id="e80b3-256">理論上，.NET 中提供的 Unicode 編碼類別 ([UTF8Encoding](xref:System.Text.UTF8Encoding)、[UnicodeEncoding](xref:System.Text.UnicodeEncoding) 和 [UTF32Encoding](xref:System.Text.UTF32Encoding)) 支援每個字元集中的每個字元，因此這些類別可以用來解決自動調整後援的問題。</span><span class="sxs-lookup"><span data-stu-id="e80b3-256">In theory, the Unicode encoding classes provided in .NET ([UTF8Encoding](xref:System.Text.UTF8Encoding), [UnicodeEncoding](xref:System.Text.UnicodeEncoding), and [UTF32Encoding](xref:System.Text.UTF32Encoding)) support every character in every character set, so they can be used to eliminate best-fit fallback issues.</span></span> 
 

<span data-ttu-id="e80b3-257">自動調整策略會因不同的字碼頁而異，並且沒有詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="e80b3-257">Best-fit strategies vary for different code pages, and they are not documented in detail.</span></span> <span data-ttu-id="e80b3-258">例如，某些字碼頁的全形拉丁字元會對應至更常見的半形拉丁字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-258">For example, for some code pages, full-width Latin characters map to the more common half-width Latin characters.</span></span> <span data-ttu-id="e80b3-259">至於其他字碼頁，則不會進行這項對應。</span><span class="sxs-lookup"><span data-stu-id="e80b3-259">For other code pages, this mapping is not made.</span></span> <span data-ttu-id="e80b3-260">即使有主動的自動調整策略，還是會有些字元在特定編碼中沒有適當的對應。</span><span class="sxs-lookup"><span data-stu-id="e80b3-260">Even under an aggressive best-fit strategy, there is no imaginable fit for some characters in some encodings.</span></span> <span data-ttu-id="e80b3-261">例如，中文表意字元在字碼頁 1252 中便沒有適當的對應。</span><span class="sxs-lookup"><span data-stu-id="e80b3-261">For example, a Chinese ideograph has no reasonable mapping to code page 1252.</span></span> <span data-ttu-id="e80b3-262">在這種情況下，會使用取代字串。</span><span class="sxs-lookup"><span data-stu-id="e80b3-262">In this case, a replacement string is used.</span></span> <span data-ttu-id="e80b3-263">根據預設，這個字串只是單一 QUESTION MARK (U+003F)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-263">By default, this string is just a single QUESTION MARK (U+003F).</span></span>

<span data-ttu-id="e80b3-264">下列範例會使用字碼頁 1252 (西歐語言的 Windows 字碼頁) 說明自動調整對應及其缺點。</span><span class="sxs-lookup"><span data-stu-id="e80b3-264">The following example uses code page 1252 (the Windows code page for Western European languages) to illustrate best-fit mapping and its drawbacks.</span></span> <span data-ttu-id="e80b3-265">[Encoding.GetEncoding(Int32](xref:System.Text.Encoding.GetEncoding(System.Int32)) 方法可用來為字碼頁 1252 擷取編碼物件。</span><span class="sxs-lookup"><span data-stu-id="e80b3-265">The [Encoding.GetEncoding(Int32](xref:System.Text.Encoding.GetEncoding(System.Int32)) method is used to retrieve an encoding object for code page 1252.</span></span> <span data-ttu-id="e80b3-266">根據預設，它會針對不支援的 Unicode 字元使用自動調整對應。</span><span class="sxs-lookup"><span data-stu-id="e80b3-266">By default, it uses a best-fit mapping for Unicode characters that it does not support.</span></span> <span data-ttu-id="e80b3-267">這個範例會執行個體化包含三個非 ASCII 字元的字串：CIRCLED LATIN CAPITAL LETTER S (U+24C8)、SUPERSCRIPT FIVE (U+2075) 和 INFINITY (U+221E) (以空格分隔)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-267">The example instantiates a string that contains three non-ASCII characters - CIRCLED LATIN CAPITAL LETTER S (U+24C8), SUPERSCRIPT FIVE (U+2075), and INFINITY (U+221E) - separated by spaces.</span></span> <span data-ttu-id="e80b3-268">如範例的輸出所示，編碼字串時，這三個原始非空格字元會被 QUESTION MARK (U+003F)、DIGIT FIVE (U+0035) 和 DIGIT EIGHT (U+0038) 取代。</span><span class="sxs-lookup"><span data-stu-id="e80b3-268">As the output from the example shows, when the string is encoded, the three original non-space characters are replaced by QUESTION MARK (U+003F), DIGIT FIVE (U+0035), and DIGIT EIGHT (U+0038).</span></span> <span data-ttu-id="e80b3-269">DIGIT EIGHT 對於不支援的 INFINITY 字元來說，是相當差的取代，QUESTION MARK 則表示沒有可供原始字元使用的對應。</span><span class="sxs-lookup"><span data-stu-id="e80b3-269">DIGIT EIGHT is a particularly poor replacement for the unsupported INFINITY character, and QUESTION MARK indicates that no mapping was available for the original character.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Get an encoding for code page 1252 (Western Europe character set).
      Encoding cp1252 = Encoding.GetEncoding(1252);

      // Define and display a string.
      string str = "\u24c8 \u2075 \u221e";
      Console.WriteLine("Original string: " + str);
      Console.Write("Code points in string: ");
      foreach (var ch in str)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");   

      // Encode a Unicode string.
      Byte[] bytes = cp1252.GetBytes(str);
      Console.Write("Encoded bytes: ");
      foreach (byte byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the string.
      string str2 = cp1252.GetString(bytes);
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2));
      if (! str.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
      }
   }
}
// The example displays the following output:
//       Original string: Ⓢ ⁵ ∞
//       Code points in string: 24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 35 20 38
//       
//       String round-tripped: False
//       ? 5 8
//       003F 0020 0035 0020 0038
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      ' Get an encoding for code page 1252 (Western Europe character set).
      Dim cp1252 As Encoding = Encoding.GetEncoding(1252)

      ' Define and display a string.
      Dim str As String = String.Format("{0} {1} {2}", ChrW(&h24c8), ChrW(&H2075), ChrW(&h221E))
      Console.WriteLine("Original string: " + str)
      Console.Write("Code points in string: ")
      For Each ch In str
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next
      Console.WriteLine()   
      Console.WriteLine()

      ' Encode a Unicode string.
      Dim bytes() As Byte = cp1252.GetBytes(str)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the string.
      Dim str2 As String = cp1252.GetString(bytes)
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2))
      If Not str.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Original string: Ⓢ ⁵ ∞
'       Code points in string: 24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 35 20 38
'       
'       String round-tripped: False
'       ? 5 8
'       003F 0020 0035 0020 0038
```

<span data-ttu-id="e80b3-270">自動調整對應是 [Encoding](xref:System.Text.Encoding) 物件的預設行為，可將 Unicode 資料編碼為字碼頁資料，有些舊版應用程式需要這個行為。</span><span class="sxs-lookup"><span data-stu-id="e80b3-270">Best-fit mapping is the default behavior for an [Encoding](xref:System.Text.Encoding) object that encodes Unicode data into code page data, and there are legacy applications that rely on this behavior.</span></span> <span data-ttu-id="e80b3-271">不過，基於安全性理由，大多數的新應用程式都應該避免自動調整行為。</span><span class="sxs-lookup"><span data-stu-id="e80b3-271">However, most new applications should avoid best-fit behavior for security reasons.</span></span> <span data-ttu-id="e80b3-272">例如，應用程式不應該透過自動調整編碼方式放入定義域名稱。</span><span class="sxs-lookup"><span data-stu-id="e80b3-272">For example, applications should not put a domain name through a best-fit encoding.</span></span>

> [!Note]
> <span data-ttu-id="e80b3-273">您也可以實作編碼的自訂自動調整後援對應。</span><span class="sxs-lookup"><span data-stu-id="e80b3-273">You can also implement a custom best-fit fallback mapping for an encoding.</span></span> <span data-ttu-id="e80b3-274">如需詳細資訊，請參閱[實作自訂後援策略](#implementing-a-custom-fallback-strategy)一節。</span><span class="sxs-lookup"><span data-stu-id="e80b3-274">For more information, see the [Implementing a custom fallback strategy](#implementing-a-custom-fallback-strategy) section.</span></span>
 
<span data-ttu-id="e80b3-275">如果自動調整後援是編碼物件的預設值，則當您藉由呼叫 [Encoding.GetEncoding(Int32, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)) 或 [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) 多載擷取 [Encoding](xref:System.Text.Encoding) 物件時，可以選擇其他後援策略。</span><span class="sxs-lookup"><span data-stu-id="e80b3-275">If best-fit fallback is the default for an encoding object, you can choose another fallback strategy when you retrieve an [Encoding](xref:System.Text.Encoding) object by calling the [Encoding.GetEncoding(Int32, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)) or [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) overload.</span></span> <span data-ttu-id="e80b3-276">下節範例會以星號 (\*)取代每一個 對應到字碼頁 1252 的字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-276">The following section includes an example that replaces each character that cannot be mapped to code page 1252 with an asterisk (\*).</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

### <a name="replacement-fallback"></a><span data-ttu-id="e80b3-277">取代後援</span><span class="sxs-lookup"><span data-stu-id="e80b3-277">Replacement fallback</span></span>

<span data-ttu-id="e80b3-278">當字元在目標配置中沒有完全相符的字元，但是沒有可以對應的適當字元時，應用程式就可以指定取代字元或字串。</span><span class="sxs-lookup"><span data-stu-id="e80b3-278">When a character does not have an exact match in the target scheme, but there is no appropriate character that it can be mapped to, the application can specify a replacement character or string.</span></span> <span data-ttu-id="e80b3-279">這是 Unicode 解碼器的預設行為，該行為會將任何無法解碼的兩個位元組序列取代為 REPLACEMENT_CHARACTER (U+FFFD)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-279">This is the default behavior for the Unicode decoder, which replaces any two-byte sequence that it cannot decode with REPLACEMENT_CHARACTER (U+FFFD).</span></span> <span data-ttu-id="e80b3-280">它也是 [ASCIIEncoding](xref:System.Text.ASCIIEncoding) 類別的預設行為，該行為會將任何無法編碼或解碼的每個字元取代為問號。</span><span class="sxs-lookup"><span data-stu-id="e80b3-280">It is also the default behavior of the [ASCIIEncoding](xref:System.Text.ASCIIEncoding) class, which replaces each character that it cannot encode or decode with a question mark.</span></span> <span data-ttu-id="e80b3-281">下列範例說明前一個範例中 Unicode 字串的字元取代。</span><span class="sxs-lookup"><span data-stu-id="e80b3-281">The following example illustrates character replacement for the Unicode string from the previous example.</span></span> <span data-ttu-id="e80b3-282">如輸出所示，每個無法解碼為 ASCII 位元組值的字元都會以 0x3F 取代，也就是以問號取代 ASCII 碼。</span><span class="sxs-lookup"><span data-stu-id="e80b3-282">As the output shows, each character that cannot be decoded into an ASCII byte value is replaced by 0x3F, which is the ASCII code for a question mark.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.ASCII;

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 3F 20 3F
//       
//       Round-trip: False
//       ? ? ?
//       003F 0020 003F 0020 003F
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.Ascii

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 3F 20 3F
'       
'       Round-trip: False
'       ? ? ?
'       003F 0020 003F 0020 003F
```

<span data-ttu-id="e80b3-283">.NET 包含 [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) 和 [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) 類別，這兩個類別會在字元無法於編碼或解碼作業中精確對應時替代取代字串。</span><span class="sxs-lookup"><span data-stu-id="e80b3-283">.NET includes the [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) and [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) classes, which substitute a replacement string if a character does not map exactly in an encoding or decoding operation.</span></span> <span data-ttu-id="e80b3-284">根據預設，這個取代字串會是一個問號，但是您可以呼叫類別建構函式多載，以便選擇不同的字串。</span><span class="sxs-lookup"><span data-stu-id="e80b3-284">By default, this replacement string is a question mark, but you can call a class constructor overload to choose a different string.</span></span> <span data-ttu-id="e80b3-285">取代字串通常 (但不一定) 是單一字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-285">Typically, the replacement string is a single character, although this is not a requirement.</span></span> <span data-ttu-id="e80b3-286">下列範例會具現化使用星號 (\*) 作為取代字串的 [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) 物件，變更字碼頁 1252 編碼器的行為。</span><span class="sxs-lookup"><span data-stu-id="e80b3-286">The following example changes the behavior of the code page 1252 encoder by instantiating an [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) object that uses an asterisk (\*) as a replacement string.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

> [!NOTE]
> <span data-ttu-id="e80b3-287">您也可以實作編碼的取代類別。</span><span class="sxs-lookup"><span data-stu-id="e80b3-287">You can also implement a replacement class for an encoding.</span></span> <span data-ttu-id="e80b3-288">如需詳細資訊，請參閱[實作自訂後援策略](#implementing-a-custom-fallback-strategy)一節。</span><span class="sxs-lookup"><span data-stu-id="e80b3-288">For more information, see the [Implementing a custom fallback strategy](#implementing-a-custom-fallback-strategy) section.</span></span>
 
<span data-ttu-id="e80b3-289">除了 QUESTION MARK (U+003F) 之外，還常使用 Unicode REPLACEMENT CHARACTER (U+FFFD) 做為取代字串，特別是當解碼無法成功轉譯成 Unicode 字元的位元組序列時。</span><span class="sxs-lookup"><span data-stu-id="e80b3-289">In addition to QUESTION MARK (U+003F), the Unicode REPLACEMENT CHARACTER (U+FFFD) is commonly used as a replacement string, particularly when decoding byte sequences that cannot be successfully translated into Unicode characters.</span></span> <span data-ttu-id="e80b3-290">不過，您可以自由選擇任何取代字串，而且該字串可以包含多個字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-290">However, you are free to choose any replacement string, and it can contain multiple characters.</span></span>

### <a name="exception-fallback"></a><span data-ttu-id="e80b3-291">例外狀況後援</span><span class="sxs-lookup"><span data-stu-id="e80b3-291">Exception fallback</span></span>

<span data-ttu-id="e80b3-292">編碼器可在無法編碼一組字元時擲回 [EncoderFallbackException](xref:System.Text.EncoderFallbackException)，而解碼器可在無法解碼位元組陣列時擲回 [DecoderFallbackException](xref:System.Text.DecoderFallbackException)，而不是提供自動調整後援或取代字串。</span><span class="sxs-lookup"><span data-stu-id="e80b3-292">Instead of providing a best-fit fallback or a replacement string, an encoder can throw an [EncoderFallbackException](xref:System.Text.EncoderFallbackException) if it is unable to encode a set of characters, and a decoder can throw a [DecoderFallbackException](xref:System.Text.DecoderFallbackException) if it is unable to decode a byte array.</span></span> <span data-ttu-id="e80b3-293">若要在編碼和解碼作業中擲回例外狀況，請將 [EncoderFallbackException](xref:System.Text.EncoderFallbackException) 物件和 [DecoderFallbackException](xref:System.Text.DecoderFallbackException) 物件分別提供給 [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) 方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-293">To throw an exception in encoding and decoding operations, you supply an [EncoderFallbackException](xref:System.Text.EncoderFallbackException) object and a [DecoderFallbackException](xref:System.Text.DecoderFallbackException) object, respectively, to the [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) method.</span></span> <span data-ttu-id="e80b3-294">下列範例說明 ASCIIEncoding 類別的例外狀況後援。</span><span class="sxs-lookup"><span data-stu-id="e80b3-294">The following example illustrates exception fallback with the ASCIIEncoding class.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", 
                                          new EncoderExceptionFallback(), 
                                          new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = {};
      try {
         bytes = enc.GetBytes(str1);
         Console.Write("Encoded bytes: ");
         foreach (var byt in bytes)
            Console.Write("{0:X2} ", byt);

         Console.WriteLine();
      }
      catch (EncoderFallbackException e) {
         Console.Write("Exception: ");
         if (e.IsUnknownSurrogate())
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index);
         else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index);
         return;
      }
      Console.WriteLine();

      // Decode the ASCII bytes.
      try {
         string str2 = enc.GetString(bytes);
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
         if (! str1.Equals(str2)) {
            Console.WriteLine(str2);
            foreach (var ch in str2)
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

            Console.WriteLine();
         } 
      }
      catch (DecoderFallbackException e) {
         Console.Write("Unable to decode byte(s) ");
         foreach (byte unknown in e.BytesUnknown)
            Console.Write("0x{0:X2} ");

         Console.WriteLine("at index {0}", e.Index);
      }
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Exception: Unable to encode 0x24C8 at index 0.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", 
                                                 New EncoderExceptionFallback(), 
                                                 New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = {}
      Try
         bytes = enc.GetBytes(str1)
         Console.Write("Encoded bytes: ")
         For Each byt In bytes
            Console.Write("{0:X2} ", byt)
         Next
         Console.WriteLine()
      Catch e As EncoderFallbackException
         Console.Write("Exception: ")
         If e.IsUnknownSurrogate() Then
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index)
         Else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index)
         End If                              
         Exit Sub
      End Try
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Try
         Dim str2 As String = enc.GetString(bytes)
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
         If Not str1.Equals(str2) Then
            Console.WriteLine(str2)
            For Each ch In str2
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
            Next    
            Console.WriteLine()
         End If 
      Catch e As DecoderFallbackException
         Console.Write("Unable to decode byte(s) ")
         For Each unknown As Byte In e.BytesUnknown
            Console.Write("0x{0:X2} ")
         Next
         Console.WriteLine("at index {0}", e.Index)
      End Try
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Exception: Unable to encode 0x24C8 at index 0.
```

> [!NOTE]
> <span data-ttu-id="e80b3-295">您也可以實作編碼作業的自訂例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="e80b3-295">You can also implement a custom exception handler for an encoding operation.</span></span> <span data-ttu-id="e80b3-296">如需詳細資訊，請參閱[實作自訂後援策略](#implementing-a-custom-fallback-strategy)一節。</span><span class="sxs-lookup"><span data-stu-id="e80b3-296">For more information, see the [Implementing a custom fallback strategy](#implementing-a-custom-fallback-strategy) section.</span></span>
 
<span data-ttu-id="e80b3-297">[EncoderFallbackException](xref:System.Text.EncoderFallbackException) 和 [DecoderFallbackException](xref:System.Text.DecoderFallbackException) 物件提供下列造成例外狀況之條件的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="e80b3-297">The [EncoderFallbackException](xref:System.Text.EncoderFallbackException) and [DecoderFallbackException](xref:System.Text.DecoderFallbackException) objects provide the following information about the condition that caused the exception:</span></span> 

* <span data-ttu-id="e80b3-298">[EncoderFallbackException](xref:System.Text.EncoderFallbackException) 物件包含 [IsUnknownSurrogate](xref:System.Text.EncoderFallbackException.IsUnknownSurrogate) 方法，這個方法會指出無法編碼的一或多個字元代表未知的 Surrogate 字組 (在這種情況下，方法會傳回 `true`)，或未知的單一字元 (在這種情況下，方法會傳回 `false`)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-298">The [EncoderFallbackException](xref:System.Text.EncoderFallbackException) object includes an [IsUnknownSurrogate](xref:System.Text.EncoderFallbackException.IsUnknownSurrogate) method, which indicates whether the character or characters that cannot be encoded represent an unknown surrogate pair (in which case, the method returns `true`) or an unknown single character (in which case, the method returns `false`).</span></span> <span data-ttu-id="e80b3-299">Surrogate 字組中的字元可從 [EncoderFallbackException.CharUnknownHigh](xref:System.Text.EncoderFallbackException.CharUnknownHigh) 和 [EncoderFallbackException.CharUnknownLow](xref:System.Text.EncoderFallbackException.CharUnknownLow) 屬性取得。</span><span class="sxs-lookup"><span data-stu-id="e80b3-299">The characters in the surrogate pair are available from the [EncoderFallbackException.CharUnknownHigh](xref:System.Text.EncoderFallbackException.CharUnknownHigh) and [EncoderFallbackException.CharUnknownLow](xref:System.Text.EncoderFallbackException.CharUnknownLow) properties.</span></span> <span data-ttu-id="e80b3-300">未知的單一字元可從 [EncoderFallbackException.CharUnknown](xref:System.Text.EncoderFallbackException.CharUnknown) 屬性取得。</span><span class="sxs-lookup"><span data-stu-id="e80b3-300">The unknown single character is available from the [EncoderFallbackException.CharUnknown](xref:System.Text.EncoderFallbackException.CharUnknown) property.</span></span> <span data-ttu-id="e80b3-301">[EncoderFallbackException.Index](xref:System.Text.EncoderFallbackException.Index) 屬性會指出字串中找到第一個無法編碼之字元的位置。</span><span class="sxs-lookup"><span data-stu-id="e80b3-301">The [EncoderFallbackException.Index](xref:System.Text.EncoderFallbackException.Index) property indicates the position in the string at which the first character that could not be encoded was found.</span></span>

* <span data-ttu-id="e80b3-302">[DecoderFallbackException](xref:System.Text.DecoderFallbackException) 物件包含 [BytesUnknown](xref:System.Text.DecoderFallbackException.BytesUnknown) 屬性，這個屬性會傳回無法解碼的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="e80b3-302">The [DecoderFallbackException](xref:System.Text.DecoderFallbackException) object includes a [BytesUnknown](xref:System.Text.DecoderFallbackException.BytesUnknown) property that returns an array of bytes that cannot be decoded.</span></span> <span data-ttu-id="e80b3-303">[DecoderFallbackException.Index](xref:System.Text.DecoderFallbackException.Index) 屬性會指出未知位元組的開始位置。</span><span class="sxs-lookup"><span data-stu-id="e80b3-303">The [DecoderFallbackException.Index](xref:System.Text.DecoderFallbackException.Index) property indicates the starting position of the unknown bytes.</span></span>

<span data-ttu-id="e80b3-304">雖然 [EncoderFallbackException](xref:System.Text.EncoderFallbackException) 和 [DecoderFallbackException](xref:System.Text.DecoderFallbackException) 物件提供了有關例外狀況的適當診斷資訊，但是並未提供編碼或解碼緩衝區的存取權。</span><span class="sxs-lookup"><span data-stu-id="e80b3-304">Although the [EncoderFallbackException](xref:System.Text.EncoderFallbackException) and [DecoderFallbackException](xref:System.Text.DecoderFallbackException) objects provide adequate diagnostic information about the exception, they do not provide access to the encoding or decoding buffer.</span></span> <span data-ttu-id="e80b3-305">因此，這兩個物件不允許在編碼或解碼方法內取代或更正無效的資料。</span><span class="sxs-lookup"><span data-stu-id="e80b3-305">Therefore, they do not allow invalid data to be replaced or corrected within the encoding or decoding method.</span></span>

## <a name="implementing-a-custom-fallback-strategy"></a><span data-ttu-id="e80b3-306">實作自訂後援策略</span><span class="sxs-lookup"><span data-stu-id="e80b3-306">Implementing a custom fallback strategy</span></span>

<span data-ttu-id="e80b3-307">除了字碼頁在內部實作的自動調整對應之外，.NET 還包括下列實作後援策略的類別：</span><span class="sxs-lookup"><span data-stu-id="e80b3-307">In addition to the best-fit mapping that is implemented internally by code pages, .NET includes the following classes for implementing a fallback strategy:</span></span>

* <span data-ttu-id="e80b3-308">使用 [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) 和 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 取代編碼作業中的字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-308">Use [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) and [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) to replace characters in encoding operations.</span></span>

* <span data-ttu-id="e80b3-309">使用 [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) 和 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 取代解碼作業中的字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-309">Use [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) to replace characters in decoding operations.</span></span>

* <span data-ttu-id="e80b3-310">在無法編碼字元時，使用 [EncoderExceptionFallback](xref:System.Text.EncoderExceptionFallback) 和 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 擲回 [EncoderFallbackException](xref:System.Text.EncoderFallbackException)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-310">Use [EncoderExceptionFallback](xref:System.Text.EncoderExceptionFallback) and [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) to throw an [EncoderFallbackException](xref:System.Text.EncoderFallbackException) when a character cannot be encoded.</span></span>

* <span data-ttu-id="e80b3-311">在無法解碼字元時，使用 [DecoderExceptionFallback](xref:System.Text.DecoderExceptionFallback) 和 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 擲回 [DecoderFallbackException](xref:System.Text.DecoderFallbackException)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-311">Use [DecoderExceptionFallback](xref:System.Text.DecoderExceptionFallback) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) to throw a [DecoderFallbackException](xref:System.Text.DecoderFallbackException) when a character cannot be decoded.</span></span>

<span data-ttu-id="e80b3-312">此外，您可以執行下列步驟，來實作使用自動調整後援、取代後援或例外狀況後援的自訂方案：</span><span class="sxs-lookup"><span data-stu-id="e80b3-312">In addition, you can implement a custom solution that uses best-fit fallback, replacement fallback, or exception fallback, by following these steps:</span></span> 

1. <span data-ttu-id="e80b3-313">針對編碼作業從 [EncoderFallback](xref:System.Text.EncoderFallback) 衍生類別，並針對解碼作業從 [DecoderFallback](xref:System.Text.DecoderFallback) 衍生類別。</span><span class="sxs-lookup"><span data-stu-id="e80b3-313">Derive a class from [EncoderFallback](xref:System.Text.EncoderFallback) for encoding operations, and from [DecoderFallback](xref:System.Text.DecoderFallback) for decoding operations.</span></span>

2. <span data-ttu-id="e80b3-314">針對編碼作業從 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 衍生類別，並針對解碼作業從 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 衍生類別。</span><span class="sxs-lookup"><span data-stu-id="e80b3-314">Derive a class from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) for encoding operations, and from [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) for decoding operations.</span></span>

3. <span data-ttu-id="e80b3-315">至於例外狀況後援，如果預先定義的 [EncoderFallbackException](xref:System.Text.EncoderFallbackException) 和 [DecoderFallbackException](xref:System.Text.DecoderFallbackException) 類別不符合您的需求，則從例外狀況物件 (例如 [Exception](xref:System.Exception) 或 [ArgumentException](xref:System.ArgumentException)) 衍生類別。</span><span class="sxs-lookup"><span data-stu-id="e80b3-315">For exception fallback, if the predefined [EncoderFallbackException](xref:System.Text.EncoderFallbackException) and [DecoderFallbackException](xref:System.Text.DecoderFallbackException) classes do not meet your needs, derive a class from an exception object such as [Exception](xref:System.Exception) or [ArgumentException](xref:System.ArgumentException).</span></span>

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a><span data-ttu-id="e80b3-316">衍生自 EncoderFallback 或 DecoderFallback</span><span class="sxs-lookup"><span data-stu-id="e80b3-316">Deriving from EncoderFallback or DecoderFallback</span></span>

<span data-ttu-id="e80b3-317">若要實作自訂後援方案，您必須針對編碼作業建立繼承自 [EncoderFallback](xref:System.Text.EncoderFallback) 的類別，以及針對解碼作業建立繼承自 [DecoderFallback](xref:System.Text.DecoderFallback) 的類別。</span><span class="sxs-lookup"><span data-stu-id="e80b3-317">To implement a custom fallback solution, you must create a class that inherits from [EncoderFallback](xref:System.Text.EncoderFallback) for encoding operations, and from [DecoderFallback](xref:System.Text.DecoderFallback) for decoding operations.</span></span> <span data-ttu-id="e80b3-318">這些類別的執行個體會傳遞給 [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) 方法，並且作為編碼類別和後援實作之間的媒介。</span><span class="sxs-lookup"><span data-stu-id="e80b3-318">Instances of these classes are passed to the [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) method and serve as the intermediary between the encoding class and the fallback implementation.</span></span>

<span data-ttu-id="e80b3-319">當您針對編碼器或解碼器建立自訂後援方案時，必須實作下列成員：</span><span class="sxs-lookup"><span data-stu-id="e80b3-319">When you create a custom fallback solution for an encoder or decoder, you must implement the following members:</span></span>

* <span data-ttu-id="e80b3-320">[EncoderFallback.MaxCharCount](xref:System.Text.EncoderFallback.MaxCharCount) 或 [DecoderFallback.MaxCharCount](xref:System.Text.DecoderFallback.MaxCharCount) 屬性，這個屬性會傳回自動調整、取代或例外狀況後援可傳回以取代單一字元的最大字元數。</span><span class="sxs-lookup"><span data-stu-id="e80b3-320">The [EncoderFallback.MaxCharCount](xref:System.Text.EncoderFallback.MaxCharCount) or [DecoderFallback.MaxCharCount](xref:System.Text.DecoderFallback.MaxCharCount) property, which returns the maximum possible number of characters that the best-fit, replacement, or exception fallback can return to replace a single character.</span></span> <span data-ttu-id="e80b3-321">若是自訂例外狀況後援，其值為零。</span><span class="sxs-lookup"><span data-stu-id="e80b3-321">For a custom exception fallback, its value is zero.</span></span> 

* <span data-ttu-id="e80b3-322">[EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) 或 [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) 方法，這個方法會傳回您自訂的 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 或 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 實作。</span><span class="sxs-lookup"><span data-stu-id="e80b3-322">The [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) or [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) method, which returns your custom [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) or [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) implementation.</span></span> <span data-ttu-id="e80b3-323">編碼器會在遇到無法成功編碼的第一個字元時呼叫這個方法，而解碼器會在遇到無法成功解碼的第一個位元組時呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-323">The method is called by the encoder when it encounters the first character that it is unable to successfully encode, or by the decoder when it encounters the first byte that it is unable to successfully decode.</span></span>

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a><span data-ttu-id="e80b3-324">衍生自 EncoderFallbackBuffer 或 DecoderFallbackBuffer</span><span class="sxs-lookup"><span data-stu-id="e80b3-324">Deriving from EncoderFallbackBuffer or DecoderFallbackBuffer</span></span>

<span data-ttu-id="e80b3-325">若要實作自訂後援方案，您還必須針對編碼作業建立繼承自 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 的類別，以及針對解碼作業建立繼承自 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 的類別。</span><span class="sxs-lookup"><span data-stu-id="e80b3-325">To implement a custom fallback solution, you must also create a class that inherits from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) for encoding operations, and from [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) for decoding operations.</span></span> <span data-ttu-id="e80b3-326">這些類別的執行個體會由 [EncoderFallback](xref:System.Text.EncoderFallback) 和 [DecoderFallback](xref:System.Text.DecoderFallback) 類別的 `CreateFallbackBuffer` 方法傳回。</span><span class="sxs-lookup"><span data-stu-id="e80b3-326">Instances of these classes are returned by the `CreateFallbackBuffer` method of the [EncoderFallback](xref:System.Text.EncoderFallback) and [DecoderFallback](xref:System.Text.DecoderFallback) classes.</span></span> <span data-ttu-id="e80b3-327">編碼器會在遇到無法編碼的第一個字元時呼叫 [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) 方法，而解碼器會在遇到無法解碼的一或多個位元組時呼叫 [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) 方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-327">The [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) method is called by the encoder when it encounters the first character that it is not able to encode, and the [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) method is called by the decoder when it encounters one or more bytes that it is not able to decode.</span></span> <span data-ttu-id="e80b3-328">[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 和 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 類別提供後援實作。</span><span class="sxs-lookup"><span data-stu-id="e80b3-328">The [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) classes provide the fallback implementation.</span></span> <span data-ttu-id="e80b3-329">每個執行個體代表包含後援字元的緩衝區，這些後援字元將取代無法編碼的字元或無法解碼的位元組序列。</span><span class="sxs-lookup"><span data-stu-id="e80b3-329">Each instance represents a buffer that contains the fallback characters that will replace the character that cannot be encoded or the byte sequence that cannot be decoded.</span></span>

<span data-ttu-id="e80b3-330">當您針對編碼器或解碼器建立自訂後援方案時，必須實作下列成員：</span><span class="sxs-lookup"><span data-stu-id="e80b3-330">When you create a custom fallback solution for an encoder or decoder, you must implement the following members:</span></span>

* <span data-ttu-id="e80b3-331">[EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.%23ctor) 或 [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) 方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-331">The [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.%23ctor) or [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) method.</span></span> <span data-ttu-id="e80b3-332">編碼器會呼叫 [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.Fallback(System.Char,System.Char,System.Int32)) 來提供後援緩衝區，其中包含無法編碼之字元的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e80b3-332">[EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.Fallback(System.Char,System.Char,System.Int32)) is called by the encoder to provide the fallback buffer with information about the character that it cannot encode.</span></span> <span data-ttu-id="e80b3-333">由於要編碼的字元可能是 Surrogate 字組，因此這個方法為多載。</span><span class="sxs-lookup"><span data-stu-id="e80b3-333">Because the character to be encoded may be a surrogate pair, this method is overloaded.</span></span> <span data-ttu-id="e80b3-334">其中一個多載會收到傳遞之要編碼的字元，以及其在字串中的索引。</span><span class="sxs-lookup"><span data-stu-id="e80b3-334">One overload is passed the character to be encoded and its index in the string.</span></span> <span data-ttu-id="e80b3-335">第二個多載會收到傳遞的高和低 Surrogate，以及其在字串中的索引。</span><span class="sxs-lookup"><span data-stu-id="e80b3-335">The second overload is passed the high and low surrogate along with its index in the string.</span></span> <span data-ttu-id="e80b3-336">解碼器會呼叫 [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) 方法來提供後援緩衝區，其中包含無法解碼之位元組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e80b3-336">The [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) method is called by the decoder to provide the fallback buffer with information about the bytes that it cannot decode.</span></span> <span data-ttu-id="e80b3-337">這個方法會收到傳遞之無法解碼的位元組陣列，以及第一個位元組的索引。</span><span class="sxs-lookup"><span data-stu-id="e80b3-337">This method is passed an array of bytes that it cannot decode, along with the index of the first byte.</span></span> <span data-ttu-id="e80b3-338">如果後援緩衝區可以提供自動調整或一或多個取代字元，則後援方法應該傳回 `true`，否則應該傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="e80b3-338">The fallback method should return `true` if the fallback buffer can supply a best-fit or replacement character or characters; otherwise, it should return `false`.</span></span> <span data-ttu-id="e80b3-339">若是例外狀況後援，後援方法應該擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e80b3-339">For an exception fallback, the fallback method should throw an exception.</span></span>

* <span data-ttu-id="e80b3-340">[EncoderFallbackBuffer.GetNextChar](xref:System.Text.EncoderFallbackBuffer.GetNextChar) 或 [DecoderFallbackBuffer.GetNextChar](xref:System.Text.DecoderFallbackBuffer.GetNextChar) 方法，編碼器或解碼器會重複呼叫這個方法，以便從後援緩衝區取得下一個字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-340">The [EncoderFallbackBuffer.GetNextChar](xref:System.Text.EncoderFallbackBuffer.GetNextChar) or [DecoderFallbackBuffer.GetNextChar](xref:System.Text.DecoderFallbackBuffer.GetNextChar) method, which is called repeatedly by the encoder or decoder to get the next character from the fallback buffer.</span></span> <span data-ttu-id="e80b3-341">當所有後援字元都已傳回時，這個方法應傳回 U+0000。</span><span class="sxs-lookup"><span data-stu-id="e80b3-341">When all fallback characters have been returned, the method should return U+0000.</span></span> 

* <span data-ttu-id="e80b3-342">[EncoderFallbackBuffer.Remaining](xref:System.Text.EncoderFallbackBuffer.Remaining) 或 [DecoderFallbackBuffer.Remaining](xref:System.Text.DecoderFallbackBuffer.Remaining) 屬性，這個屬性會傳回後援緩衝區中剩餘的字元數。</span><span class="sxs-lookup"><span data-stu-id="e80b3-342">The [EncoderFallbackBuffer.Remaining](xref:System.Text.EncoderFallbackBuffer.Remaining) or [DecoderFallbackBuffer.Remaining](xref:System.Text.DecoderFallbackBuffer.Remaining) property, which returns the number of characters remaining in the fallback buffer.</span></span>

* <span data-ttu-id="e80b3-343">[EncoderFallbackBuffer.MovePrevious](xref:System.Text.EncoderFallbackBuffer.MovePrevious) 或 [DecoderFallbackBuffer.MovePrevious](xref:System.Text.DecoderFallbackBuffer.MovePrevious) 方法，這個方法會將後援緩衝區中的目前位置移至前一個字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-343">The [EncoderFallbackBuffer.MovePrevious](xref:System.Text.EncoderFallbackBuffer.MovePrevious) or [DecoderFallbackBuffer.MovePrevious](xref:System.Text.DecoderFallbackBuffer.MovePrevious) method, which moves the current position in the fallback buffer to the previous character.</span></span>

* <span data-ttu-id="e80b3-344">[EncoderFallbackBuffer.Reset](xref:System.Text.EncoderFallbackBuffer.Reset) 或 [DecoderFallbackBuffer.Reset](xref:System.Text.DecoderFallbackBuffer.Reset) 方法，這個方法會重新初始化後援緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e80b3-344">The [EncoderFallbackBuffer.Reset](xref:System.Text.EncoderFallbackBuffer.Reset) or [DecoderFallbackBuffer.Reset](xref:System.Text.DecoderFallbackBuffer.Reset) method, which reinitializes the fallback buffer.</span></span>

<span data-ttu-id="e80b3-345">如果後援實作是自動調整後援或取代後援，則衍生自 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 和 [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) 的類別還會維護兩個私用執行個體欄位：緩衝區中確實的字元數，以及緩衝區中要傳回之下一個字元的索引。</span><span class="sxs-lookup"><span data-stu-id="e80b3-345">If the fallback implementation is a best-fit fallback or a replacement fallback, the classes derived from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) also maintain two private instance fields: the exact number of characters in the buffer; and the index of the next character in the buffer to return.</span></span>

### <a name="an-encoderfallback-example"></a><span data-ttu-id="e80b3-346">EncoderFallback 範例</span><span class="sxs-lookup"><span data-stu-id="e80b3-346">An EncoderFallback example</span></span>

<span data-ttu-id="e80b3-347">前文中的範例使用了取代後援，以星號 (\*) 取代無法對應到 ASCII 字元的 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-347">An earlier example used replacement fallback to replace Unicode characters that did not correspond to ASCII characters with an asterisk (\*).</span></span> <span data-ttu-id="e80b3-348">下列範例使用自訂自動調整後援實作，而不是提供較佳的非 ASCII 字元對應。</span><span class="sxs-lookup"><span data-stu-id="e80b3-348">The following example uses a custom best-fit fallback implementation instead to provide a better mapping of non-ASCII characters.</span></span>

<span data-ttu-id="e80b3-349">下列程式碼會定義名為 `CustomMapper` 的類別，該類別衍生自 [EncoderFallback](xref:System.Text.EncoderFallback)，會處理非 ASCII 字元的自動調整對應。</span><span class="sxs-lookup"><span data-stu-id="e80b3-349">The following code defines a class named `CustomMapper` that is derived from [EncoderFallback](xref:System.Text.EncoderFallback) to handle the best-fit mapping of non-ASCII characters.</span></span> <span data-ttu-id="e80b3-350">其 `CreateFallbackBuffer` 方法會傳回提供 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) 實作的 `CustomMapperFallbackBuffer` 物件。</span><span class="sxs-lookup"><span data-stu-id="e80b3-350">Its `CreateFallbackBuffer` method returns a `CustomMapperFallbackBuffer` object, which provides the [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) implementation.</span></span> <span data-ttu-id="e80b3-351">`CustomMapper` 類別使用 [Dictionary&lt;TKey, TValue&gt;](xref:System.Collections.Generic.Dictionary%602) 物件來儲存不支援的 Unicode 字元對應 (機碼值) 及其對應的 8 位元字元 (儲存在 64 位元整數的兩個連續的位元組中)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-351">The `CustomMapper` class uses a [Dictionary&lt;TKey, TValue&gt;](xref:System.Collections.Generic.Dictionary%602) object to store the mappings of unsupported Unicode characters (the key value) and their corresponding 8-bit characters (which are stored in two consecutive bytes in a 64-bit integer).</span></span> <span data-ttu-id="e80b3-352">為了讓後援緩衝區可以使用這項對應，`CustomMapper` 執行個體會當做參數傳遞給 `CustomMapperFallbackBuffer` 類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="e80b3-352">To make this mapping available to the fallback buffer, the `CustomMapper` instance is passed as a parameter to the `CustomMapperFallbackBuffer` class constructor.</span></span> <span data-ttu-id="e80b3-353">由於最長的對應是代表 Unicode 字元 U+221E 的字串 "INF"，因此 `MaxCharCount` 屬性會傳回 3。</span><span class="sxs-lookup"><span data-stu-id="e80b3-353">Because the longest mapping is the string "INF" for the Unicode character U+221E, the `MaxCharCount` property returns 3.</span></span> 

```csharp
public class CustomMapper : EncoderFallback
{
   public string DefaultString;
   internal Dictionary<ushort, ulong> mapping;

   public CustomMapper() : this("*")
   {   
   }

   public CustomMapper(string defaultString)
   {
      this.DefaultString = defaultString;

      // Create table of mappings
      mapping = new Dictionary<ushort, ulong>();
      mapping.Add(0x24C8, 0x53);
      mapping.Add(0x2075, 0x35);
      mapping.Add(0x221E, 0x49004E0046);
   }

   public override EncoderFallbackBuffer CreateFallbackBuffer()
   {
      return new CustomMapperFallbackBuffer(this);
   }

   public override int MaxCharCount
   {
      get { return 3; }
   } 
}
```

```vb
Public Class CustomMapper : Inherits EncoderFallback
   Public DefaultString As String
   Friend mapping As Dictionary(Of UShort, ULong)

   Public Sub New()
      Me.New("?")
   End Sub

   Public Sub New(ByVal defaultString As String)
      Me.DefaultString = defaultString

      ' Create table of mappings
      mapping = New Dictionary(Of UShort, ULong)
      mapping.Add(&H24C8, &H53)
      mapping.Add(&H2075, &H35)
      mapping.Add(&H221E, &H49004E0046)
   End Sub

   Public Overrides Function CreateFallbackBuffer() As System.Text.EncoderFallbackBuffer
      Return New CustomMapperFallbackBuffer(Me)
   End Function

   Public Overrides ReadOnly Property MaxCharCount As Integer
      Get
         Return 3
      End Get
   End Property
End Class
```

<span data-ttu-id="e80b3-354">下列程式碼會定義 `CustomMapperFallbackBuffer` 類別，該類別衍生自 [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer)。</span><span class="sxs-lookup"><span data-stu-id="e80b3-354">The following code defines the `CustomMapperFallbackBuffer` class, which is derived from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer).</span></span> <span data-ttu-id="e80b3-355">包含自動調整對應並在 `CustomMapper` 執行個體中定義的字典可從其類別建構函式取得。</span><span class="sxs-lookup"><span data-stu-id="e80b3-355">The dictionary that contains best-fit mappings and that is defined in the `CustomMapper` instance is available from its class constructor.</span></span> <span data-ttu-id="e80b3-356">如果 ASCII 編碼器無法編碼的任何 Unicode 字元是在對應字典中定義，則其 `Fallback` 方法會傳回 `true`，否則會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="e80b3-356">Its `Fallback` method returns `true` if any of the Unicode characters that the ASCII encoder cannot encode are defined in the mapping dictionary; otherwise, it returns `false`.</span></span> <span data-ttu-id="e80b3-357">針對每個後援，私用 `count` 變數會指出要傳回的剩餘字元數，而私用 `index` 變數會指出要傳回的下一個字元在字串緩衝區 `charsToReturn` 中的位置。</span><span class="sxs-lookup"><span data-stu-id="e80b3-357">For each fallback, the private `count` variable indicates the number of characters that remain to be returned, and the private `index` variable indicates the position in the string buffer, `charsToReturn`, of the next character to return.</span></span> 

```csharp
public class CustomMapperFallbackBuffer : EncoderFallbackBuffer
{
   int count = -1;                   // Number of characters to return
   int index = -1;                   // Index of character to return
   CustomMapper fb; 
   string charsToReturn; 

   public CustomMapperFallbackBuffer(CustomMapper fallback)
   {
      this.fb = fallback;
   }

   public override bool Fallback(char charUnknownHigh, char charUnknownLow, int index)
   {
      // Do not try to map surrogates to ASCII.
      return false;
   }

   public override bool Fallback(char charUnknown, int index)
   {
      // Return false if there are already characters to map.
      if (count >= 1) return false;

      // Determine number of characters to return.
      charsToReturn = String.Empty;

      ushort key = Convert.ToUInt16(charUnknown);
      if (fb.mapping.ContainsKey(key)) {
         byte[] bytes = BitConverter.GetBytes(fb.mapping[key]);
         int ctr = 0;
         foreach (var byt in bytes) {
            if (byt > 0) {
               ctr++;
               charsToReturn += (char) byt;
            }
         }
         count = ctr;
      }
      else {
         // Return default.
         charsToReturn = fb.DefaultString;
         count = 1;
      }
      this.index = charsToReturn.Length - 1;

      return true;
   }

   public override char GetNextChar()
   {
      // We'll return a character if possible, so subtract from the count of chars to return.
      count--;
      // If count is less than zero, we've returned all characters.
      if (count < 0) 
         return '\u0000';

      this.index--;
      return charsToReturn[this.index + 1];
   }

   public override bool MovePrevious()
   {
      // Original: if count >= -1 and pos >= 0
      if (count >= -1) {
         count++;
         return true;
      }
      else {
         return false;
      }
   }

   public override int Remaining 
   {
      get { return count < 0 ? 0 : count; }
   }

   public override void Reset()
   {
      count = -1;
      index = -1;
   }
}
```

```vb
Public Class CustomMapperFallbackBuffer : Inherits EncoderFallbackBuffer

   Dim count As Integer = -1        ' Number of characters to return
   Dim index As Integer = -1        ' Index of character to return
   Dim fb As CustomMapper
   Dim charsToReturn As String

   Public Sub New(ByVal fallback As CustomMapper)
      MyBase.New()
      Me.fb = fallback
   End Sub

   Public Overloads Overrides Function Fallback(ByVal charUnknownHigh As Char, ByVal charUnknownLow As Char, ByVal index As Integer) As Boolean
      ' Do not try to map surrogates to ASCII.
      Return False
   End Function

   Public Overloads Overrides Function Fallback(ByVal charUnknown As Char, ByVal index As Integer) As Boolean
      ' Return false if there are already characters to map.
      If count >= 1 Then Return False

      ' Determine number of characters to return.
      charsToReturn = String.Empty

      Dim key As UShort = Convert.ToUInt16(charUnknown)
      If fb.mapping.ContainsKey(key) Then
         Dim bytes() As Byte = BitConverter.GetBytes(fb.mapping.Item(key))
         Dim ctr As Integer
         For Each byt In bytes
            If byt > 0 Then
               ctr += 1
               charsToReturn += Chr(byt)
            End If
         Next
         count = ctr
      Else
         ' Return default.
         charsToReturn = fb.DefaultString
         count = 1
      End If
      Me.index = charsToReturn.Length - 1

      Return True
   End Function

   Public Overrides Function GetNextChar() As Char
      ' We'll return a character if possible, so subtract from the count of chars to return.
      count -= 1
      ' If count is less than zero, we've returned all characters.
      If count < 0 Then Return ChrW(0)

      Me.index -= 1
      Return charsToReturn(Me.index + 1)
   End Function

   Public Overrides Function MovePrevious() As Boolean
      ' Original: if count >= -1 and pos >= 0
      If count >= -1 Then
         count += 1
         Return True
      Else
         Return False
      End If
   End Function

   Public Overrides ReadOnly Property Remaining As Integer
      Get
         Return If(count < 0, 0, count)
      End Get
   End Property

   Public Overrides Sub Reset()
      count = -1
      index = -1
   End Sub
End Class
```

<span data-ttu-id="e80b3-358">接著，下列程式碼會執行個體化 `CustomMapper` 物件，並將該物件的執行個體傳遞給 [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) 方法。</span><span class="sxs-lookup"><span data-stu-id="e80b3-358">The following code then instantiates the `CustomMapper` object and passes an instance of it to the [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) method.</span></span> <span data-ttu-id="e80b3-359">輸出會指出，自動調整後援實作成功處理原始字串中這三個非 ASCII 字元。</span><span class="sxs-lookup"><span data-stu-id="e80b3-359">The output indicates that the best-fit fallback implementation successfully handles the three non-ASCII characters in the original string.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Text;

class Program
{
   static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", new CustomMapper(), new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      for (int ctr = 0; ctr <= str1.Length - 1; ctr++) {
         Console.Write("{0} ", Convert.ToUInt16(str1[ctr]).ToString("X4"));
         if (ctr == str1.Length - 1) 
            Console.WriteLine();
      }
      Console.WriteLine();

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);

      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      }
   }
}
```

```vb
Imports System.Text
Imports System.Collections.Generic

Module Module1

   Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", New CustomMapper(), New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&H24C8), ChrW(&H2075), ChrW(&H221E))
      Console.WriteLine(str1)
      For ctr As Integer = 0 To str1.Length - 1
         Console.Write("{0} ", Convert.ToUInt16(str1(ctr)).ToString("X4"))
         If ctr = str1.Length - 1 Then Console.WriteLine()
      Next
      Console.WriteLine()

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="e80b3-360">請參閱</span><span class="sxs-lookup"><span data-stu-id="e80b3-360">See also</span></span>

[<span data-ttu-id="e80b3-361">System.Text.Encoder</span><span class="sxs-lookup"><span data-stu-id="e80b3-361">System.Text.Encoder</span></span>](xref:System.Text.Encoder)

[<span data-ttu-id="e80b3-362">System.Text.EncoderFallback</span><span class="sxs-lookup"><span data-stu-id="e80b3-362">System.Text.EncoderFallback</span></span>](xref:System.Text.EncoderFallback)

[<span data-ttu-id="e80b3-363">System.Text.Decoder</span><span class="sxs-lookup"><span data-stu-id="e80b3-363">System.Text.Decoder</span></span>](xref:System.Text.Decoder)

[<span data-ttu-id="e80b3-364">System.Text.DecoderFallback</span><span class="sxs-lookup"><span data-stu-id="e80b3-364">System.Text.DecoderFallback</span></span>](xref:System.Text.DecoderFallback)

[<span data-ttu-id="e80b3-365">System.Text.Encoding</span><span class="sxs-lookup"><span data-stu-id="e80b3-365">System.Text.Encoding</span></span>](xref:System.Text.Encoding)





