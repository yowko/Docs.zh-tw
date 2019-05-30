---
title: .NET 中的字元編碼
description: 了解 .NET 中的編碼及解碼字元。
ms.date: 12/22/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoding, understanding
- encoding, choosing
- encoding, fallback strategy
ms.assetid: bf6d9823-4c2d-48af-b280-919c5af66ae9
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: ac4de843b3a134b840fc37e3c1d8327fe0010d79
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960327"
---
# <a name="character-encoding-in-net"></a>.NET 中的字元編碼
字元是可以用許多不同的方式來表示的抽象實體。 字元編碼是一套系統，可將所支援之字元集中的每個字元與代表該字元的特定值配對。 例如，摩斯密碼就是一種字元編碼，可將羅馬字母中的每個字元與適合透過電報線路傳輸的點和虛線圖樣配對。 電腦的字元編碼可將所支援之字元集中的每個字元與代表該字元的數值配對。 字元編碼包含兩個不同的元件：  
  
- 編碼器，可將字元序列轉譯成數值 (位元組) 序列。  
  
- 解碼器，可將位元組序列轉譯成字元序列。  
  
 字元編碼描述編碼器和解碼器運作時所依據的規則。 例如， <xref:System.Text.UTF8Encoding> 類別描述編碼和解碼 8 位元 Unicode 轉換格式 (UTF-8) 的規則，該格式使用一到四個位元組來表示單一 Unicode 字元。 編碼和解碼也可包含驗證。 例如， <xref:System.Text.UnicodeEncoding> 類別會檢查所有 Surrogate，確定它們是由有效的 Surrogate 字組所組成。 (Surrogate 字組是由包含範圍從 U+D800 到 U+DBFF 之字碼指標的字元，後面接著包含範圍從 U+DC00 到 U+DFFF 之字碼指標的字元所組成)。後援策略決定編碼器如何處理無效的字元，或解碼器如何處理無效的位元組。  
  
> [!WARNING]
>  .NET 編碼類別提供儲存和轉換字元資料的方法。 這些類別不應用來儲存字串格式的二進位資料。 根據使用的編碼方式，使用編碼類別將二進位資料轉換成字串格式可能會導致未預期的行為，並且產生不正確或損毀的資料。 若要將二進位資料轉換成字串格式，請使用 <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> 方法。  
  
 .NET 使用 UTF-16 編碼 (以 <xref:System.Text.UnicodeEncoding> 類別表示) 來表示字元和字串。 以 Common Language Runtime 為目標的應用程式使用編碼器將 Common Language Runtime 所支援的 Unicode 字元表示對應至其他編碼配置， 並使用解碼器將非 Unicode 編碼的字元對應至 Unicode。  
  
 本主題包含下列章節：  
  
- [.NET 中的編碼](../../../docs/standard/base-types/character-encoding.md#Encodings)  
  
- [選取編碼類別](../../../docs/standard/base-types/character-encoding.md#Selecting)  
  
- [使用編碼物件](../../../docs/standard/base-types/character-encoding.md#Using)  
  
- [選擇後援策略](../../../docs/standard/base-types/character-encoding.md#FallbackStrategy)  
  
- [Implementing a Custom Fallback Strategy](../../../docs/standard/base-types/character-encoding.md#Custom)  
  
<a name="Encodings"></a>   
## <a name="encodings-in-net"></a>.NET 中的編碼  
 .NET 中的所有字元編碼類別都會繼承自 <xref:System.Text.Encoding?displayProperty=nameWithType> 類別，這是定義所有字元編碼共通功能的抽象類別。 若要存取 .NET 中實作的個別編碼物件，請執行下列作業：  
  
- 使用 <xref:System.Text.Encoding> 類別的靜態屬性，這些屬性會傳回代表 .NET 中可用之標準字元編碼 (ASCII、UTF-7、UTF-8、UTF-16 和 UTF-32) 的物件。 例如， <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> 屬性會傳回 <xref:System.Text.UnicodeEncoding> 物件。 每個物件會使用取代後援，來處理無法編碼的字串和無法解碼的位元組。 (如需詳細資訊，請參閱 [Replacement Fallback](../../../docs/standard/base-types/character-encoding.md#Replacement) 一節。)  
  
- 呼叫編碼的類別建構函式。 ASCII、UTF-7、UTF-8、UTF-16 和 UTF-32 編碼的物件可以透過這種方式執行個體化。 每個物件預設會使用取代後援，來處理無法編碼的字串和無法解碼的位元組，不過您可以指定改為擲回例外狀況。 (如需詳細資訊，請參閱 [Replacement Fallback](../../../docs/standard/base-types/character-encoding.md#Replacement) 和 [Exception Fallback](../../../docs/standard/base-types/character-encoding.md#Exception) 一節。)  
  
- 呼叫 <xref:System.Text.Encoding.%23ctor%28System.Int32%29?displayProperty=nameWithType> 建構函式，並將代表編碼的整數傳遞給該建構函式。 標準編碼物件使用取代後援，來處理無法編碼的字串和無法解碼的位元組，而字碼頁和雙位元組字元集 (DBCS) 編碼物件則是使用自動調整後援。 (如需詳細資訊，請參閱 [Best-Fit Fallback](../../../docs/standard/base-types/character-encoding.md#BestFit) 一節。)  
  
- 呼叫 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 方法，這個方法會傳回 .NET 中可用的任何標準、字碼頁或 DBCS 編碼。 多載可讓您同時為編碼器和解碼器指定後援物件。  
  
> [!NOTE]
>  Unicode 標準會對每個受支援字集中的每個字元，指派一個字碼指標 (數字) 和一個名稱。 例如，字元 "A" 是由字碼指標 U+0041 和名稱 "LATIN CAPITAL LETTER A" 來表示。 Unicode 轉換格式 (UTF) 編碼定義將字碼指標編碼為一或多個位元組序列的方式。 Unicode 編碼配置簡化全球化應用程式的開發作業，因為它能夠以單一編碼表示任何字元集的字元。 應用程式開發人員不再需要追蹤用來產生特定語言或書寫系統字元的編碼配置，同時資料可在各國系統之間共用，而不會損毀。  
>   
>  .NET 支援由 Unicode 標準定義的三種編碼：UTF-8、UTF-16 和 UTF-32。 如需詳細資訊，請參閱 [Unicode 首頁](https://www.unicode.org/) \(英文\) 的＜Unicode 標準＞。  
  
 您可以藉由呼叫 <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> 方法，來擷取 .NET 中所有可用編碼的相關資訊。 .NET 支援下表所列的字元編碼系統。  
  
|編碼|類別|說明|優點/缺點|  
|--------------|-----------|-----------------|-------------------------------|  
|ASCII|<xref:System.Text.ASCIIEncoding>|使用位元組較低的七個位元編碼有限範圍的字元。|由於這個編碼僅支援 U+0000 到 U+007F 之間的字元值，因此大部分的情況下並不適用於國際化的應用程式。|  
|UTF-7|<xref:System.Text.UTF7Encoding>|以 7 位元 ASCII 字元序列表示字元。 非 ASCII 的 Unicode 字元則以 ASCII 字元的逸出序列表示。|UTF-7 支援電子郵件和新聞群組通訊協定之類的通訊協定。 不過，UTF-7 並沒有特別安全或穩固。 在某些情況下，變更一個位元便可能會徹底改變整個 UTF-7 字串的解譯。 而在其他情況下，不同的 UTF-7 字串可能會編碼為相同的文字。 對於包含非 ASCII 字元的序列而言，UTF-7 比 UTF-8 需要更多空間，而且編碼/解碼的速度比較慢。 因此，您應該盡可能使用 UTF-8，而不是 UTF-7。|  
|UTF-8|<xref:System.Text.UTF8Encoding>|以一到四個位元組的序列表示每個 Unicode 字碼指標。|UTF-8 支援 8 位元的資料大小，而且適用於許多現有的作業系統。 對於 ASCII 字元範圍而言，UTF-8 與 ASCII 編碼完全相同，而且允許範圍更廣的字元集。 不過，針對中日韓 (CJK) 字集，UTF-8 可能要求每個字元需有三個位元組，而且造成的資料大小可能比 UTF-16 還大。 請注意，ASCII 資料量 (例如 HTML 標記) 有時可能是 CJK 範圍大小增加的原因。|  
|UTF-16|<xref:System.Text.UnicodeEncoding>|以一個或兩個 16 位元整數的序列表示每個 Unicode 字碼指標。 雖然 Unicode 補充字元 (U+10000 及以上) 需要兩個 UTF-16 Surrogate 字碼指標，但最常用的 Unicode 字元只需要一個 UTF-16 字碼指標。 同時支援位元組由小到大和位元組由大到小的位元組順序。|Common Language Runtime 會使用 UTF-16 編碼表示 <xref:System.Char> 和 <xref:System.String> 值，而 Windows 作業系統會使用該編碼表示 `WCHAR` 值。|  
|UTF-32|<xref:System.Text.UTF32Encoding>|以 32 位元整數表示每個 Unicode 字碼指標。 同時支援位元組由小到大和位元組由大到小的位元組順序。|當編碼空間對作業系統十分重要，而應用程式想要在作業系統上避免 UTF-16 編碼的 Surrogate 字碼指標行為時，可以使用 UTF-32 編碼。 畫面上呈現的單一字符仍然可以使用一個以上的 UTF-32 字元編碼。|  
|ANSI/ISO 編碼||提供各種字碼頁的支援。 在 Windows 作業系統上，字碼頁是用來支援特定語言或語言群組。 如需列出 .NET 所支援之字碼頁的表格，請參閱 <xref:System.Text.Encoding> 類別。 您可以藉由呼叫 <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> 方法，為特定字碼頁擷取編碼物件。|字碼頁包含 256 個字碼指標，並且以零起始。 在大部分的字碼頁中，0 到 127 的字碼指標代表 ASCII 字元集，而各字碼頁的 128 到 255 字碼指標則有很大的差異。 例如，字碼頁 1252 提供拉丁書寫系統 (包括英文、德文和法文) 的字元。 字碼頁 1252 中的最後 128 個字碼指標含有強調文字字元。 字碼頁 1253 提供希臘文書寫系統所需的字元碼。 字碼頁 1253 中的最後 128 個字碼指標含有希臘文字元。 因此，採用 ANSI 字碼頁的應用程式無法將希臘文和德文儲存在相同的文字資料流中，除非它包含了表示參考字碼頁的識別項。|  
|雙位元組字元集 (DBCS) 編碼||支援包含超過 256 個字元的語言，例如中文、日文和韓文。 在 DBCS 中，一組字碼指標 (一個雙位元組) 會代表一個字元。 <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> 屬性會針對 DBCS 編碼傳回 `false` 。 您可以藉由呼叫 <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> 方法，為特定 DBCS 擷取編碼物件。|在 DBCS 中，一組字碼指標 (一個雙位元組) 會代表一個字元。 當應用程式處理 DBCS 資料時，DBCS 字元的第一個位元組 (前導位元組) 會與緊接在它後面的後隨位元組一起處理。 由於單獨一組雙位元組字碼指標可依據字碼頁表示不同的字元，因此這個配置仍然不允許在相同資料流中結合兩種語言，例如日文和中文。|  
  
 這些編碼可讓您處理 Unicode 字元，以及舊版應用程式中最常用的編碼。 此外，您可以藉由定義衍生自 <xref:System.Text.Encoding> 的類別及覆寫其成員，來建立自訂編碼。  
  
### <a name="platform-notes-net-core"></a>平台注意事項：.NET Core  
 根據預設，除了字碼頁 28591 以及UTF-8 和 UTF-16 等 Unicode 編碼之外，.NET Core 不會提供任何字碼頁編碼。 不過，您可將在以 .NET 為目標的標準 Windows 應用程式中找到的字碼頁編碼，加入至您的應用程式。 如需完整資訊，請參閱 <xref:System.Text.CodePagesEncodingProvider> 主題。  
  
<a name="Selecting"></a>   
## <a name="selecting-an-encoding-class"></a>選取編碼類別  
 如果您有機會選擇應用程式使用的編碼，則應該使用 Unicode 編碼，最好是 <xref:System.Text.UTF8Encoding> 或 <xref:System.Text.UnicodeEncoding> (.NET 也支援第三種 Unicode 編碼 <xref:System.Text.UTF32Encoding>)。  
  
 如果您打算使用 ASCII 編碼 (<xref:System.Text.ASCIIEncoding>)，請改為選擇 <xref:System.Text.UTF8Encoding> 。 這兩種編碼對於 ASCII 字元集而言完全相同，但是 <xref:System.Text.UTF8Encoding> 具有下列優點：  
  
- 它可以表示每個 Unicode 字元，而 <xref:System.Text.ASCIIEncoding> 只支援 U+0000 與 U+007F 之間的 Unicode 字元值。  
  
- 它提供錯誤偵測且具有較佳的安全性。  
  
- 它已調整成其可能的最快速度，因此在速度上應該會超過其他任何編碼。 即使為全部都是 ASCII 的內容，使用 <xref:System.Text.UTF8Encoding> 執行的作業也會快過使用 <xref:System.Text.ASCIIEncoding>執行的作業。  
  
 您應該考慮只對舊版應用程式使用 <xref:System.Text.ASCIIEncoding> 。 不過，即使是舊版應用程式， <xref:System.Text.UTF8Encoding> 仍然可能是較佳的選擇，原因如下 (假設使用預設值)：  
  
- 如果您的應用程式具有的內容不完全是 ASCII，而且使用 <xref:System.Text.ASCIIEncoding>編碼該內容，則每個非 ASCII 字元都會編碼為問號 (?)。 如果應用程式接著解碼這份資料，資訊就會遺失。  
  
- 如果應用程式具有的內容不完全是 ASCII，而且使用 <xref:System.Text.UTF8Encoding>編碼該內容，將結果解譯為 ASCII 會難以理解。 不過，如果應用程式接著使用 UTF-8 解碼器來解碼這份資料，則該資料會成功地執行來回轉換。  
  
 在 Web 應用程式中，傳送至用戶端以回應 Web 要求的字元應該反映用戶端上使用的編碼。 在大部分情況下，您應該將 <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType> 屬性所傳回的值，以便以使用者預期的編碼方式來顯示文字。  
  
<a name="Using"></a>   
## <a name="using-an-encoding-object"></a>使用編碼物件  
 編碼器會將字元字串 (最常見為 Unicode 字元) 轉換成其對等數值 (位元組)。 例如，您可能使用 ASCII 編碼器將 Unicode 字元轉換成 ASCII，以便在主控台上顯示。 若要執行轉換，請呼叫 <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType> 方法。 如果您想要在執行編碼之前判斷儲存編碼的字元需要多少個位元組，可以呼叫 <xref:System.Text.Encoding.GetByteCount%2A> 方法。  
  
 下列範例會在兩項不同的作業中使用單一位元組陣列編碼字串。 它會保留一個索引，指出下一組 ASCII 編碼位元組在位元組陣列中的開始位置。 它會呼叫 <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType> 方法，確保位元組陣列的大小夠大，足以容納編碼的字串。 然後它會呼叫 <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> 方法來編碼字串中的字元。  
  
 [!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
 [!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]  
  
 解碼器會將反映特定字元編碼的位元組陣列轉換成字元陣列或字串中的字元集。 若要將位元組陣列解碼為字元陣列，請呼叫 <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> 方法。 若要將位元組陣列解碼為字串，請呼叫 <xref:System.Text.Encoding.GetString%2A> 方法。 如果您想要在執行解碼之前判斷儲存解碼的位元組需要多少個字元，可以呼叫 <xref:System.Text.Encoding.GetCharCount%2A> 方法。  
  
 下列範例會編碼三個字串，然後將這些字串解碼為單一字元陣列。 它會保留一個索引，指出下一組解碼的字元在字元陣列中的開始位置。 它會呼叫 <xref:System.Text.ASCIIEncoding.GetCharCount%2A> 方法，確保字元陣列的大小夠大，足以容納所有解碼的字元。 然後它會呼叫 <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> 方法來解碼位元組陣列。  
  
 [!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
 [!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]  
  
 衍生自 <xref:System.Text.Encoding> 之類別的編碼和解碼方法設計成可處理一組完整的資料；也就是說，單一方法呼叫中會提供所有要編碼或解碼的資料。 不過，在某些情況下，資料是以資料流提供，因此只能從個別讀取作業取得要編碼或解碼的資料。 因此，編碼或解碼作業必須記住之前叫用時的任何儲存狀態。 衍生自 <xref:System.Text.Encoder> 和 <xref:System.Text.Decoder> 之類別的方法能夠處理橫跨多個方法呼叫的編碼和解碼作業。  
  
 特定編碼的 <xref:System.Text.Encoder> 物件可從該編碼的 <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> 屬性取得。 特定編碼的 <xref:System.Text.Decoder> 物件可從該編碼的 <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> 屬性取得。 若為解碼作業，請注意衍生自 <xref:System.Text.Decoder> 的類別包含 <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> 方法，但是沒有對應至 <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>的方法。  
  
 下列範例說明使用 <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> 和 <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> 方法解碼 Unicode 位元組陣列的差異。 這個範例會將包含某些 Unicode 字元的字串編碼為檔案，然後使用這兩種解碼方法進行解碼，且一次解碼十個位元組。 由於 Surrogate 字組會在第十個和第十一個位元組發生，因此會在不同的方法呼叫中另外解碼。 如輸出所示， <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> 方法無法正確解碼位元組，而是將它們取代為 U+FFFD (REPLACEMENT CHARACTER)。 另一方面， <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> 方法能夠成功解碼位元組陣列並取得原始字串。  
  
 [!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
 [!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]  
  
<a name="FallbackStrategy"></a>   
## <a name="choosing-a-fallback-strategy"></a>選擇後援策略  
 當某個方法嘗試編碼或解碼字元，但是沒有任何對應存在時，它就必須實作後援策略，以決定應該如何處理失敗的對應。 後援策略有三種類型：  
  
- Best-Fit Fallback  
  
- Replacement Fallback  
  
- Exception Fallback  
  
> [!IMPORTANT]
>  編碼作業最常在 Unicode 字元無法對應至特定字碼頁編碼時發生問題。 解碼作業最常在無效的位元組序列無法轉譯為有效的 Unicode 字元時發生問題。 因此，您應該知道特定編碼物件所使用的後援策略。 您應該在執行個體化編碼物件時，盡可能指定該物件所使用的後援策略。  
  
<a name="BestFit"></a>   
### <a name="best-fit-fallback"></a>Best-Fit Fallback  
 當字元在目標編碼中沒有完全相符的字元時，編碼器可以嘗試將該字元對應至類似的字元 (自動調整後援大部分是針對編碼問題，而不是針對解碼問題。 很少有字碼頁包含無法成功對應至 Unicode 的字元)。自動調整後援是 <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> 和 <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> 多載所擷取之字碼頁和雙位元組字元集編碼的預設值。  
  
> [!NOTE]
>  理論上，.NET 中提供的 Unicode 編碼類別 (<xref:System.Text.UTF8Encoding>、<xref:System.Text.UnicodeEncoding> 和 <xref:System.Text.UTF32Encoding>) 支援每個字元集中的每個字元，因此這些類別可以用來解決自動調整後援的問題。  
  
 自動調整的策略會因不同的字碼頁而異。 例如，某些字碼頁的全形拉丁字元會對應至更常見的半形拉丁字元。 至於其他字碼頁，則不會進行這項對應。 即使有主動的自動調整策略，還是會有些字元在特定編碼中沒有適當的對應。 例如，中文表意字元在字碼頁 1252 中便沒有適當的對應。 在這種情況下，會使用取代字串。 根據預設，這個字串只是單一 QUESTION MARK (U+003F)。  
  
> [!NOTE]
>  自動調整的策略不會詳細記錄。 不過，[Unicode Consortium](https://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) \(英文\) 網站上記載了數個字碼頁。 請檢閱該資料夾的 **readme.txt** 檔案，以取得如何解譯對應檔案的說明。
  
 下列範例會使用字碼頁 1252 (西歐語言的 Windows 字碼頁) 說明自動調整對應及其缺點。 <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> 方法可用來為字碼頁 1252 擷取編碼物件。 根據預設，它會針對不支援的 Unicode 字元使用自動調整對應。 這個範例會執行個體化包含三個非 ASCII 字元的字串：CIRCLED LATIN CAPITAL LETTER S (U+24C8)、SUPERSCRIPT FIVE (U+2075) 和 INFINITY (U+221E) (以空格分隔)。 如範例的輸出所示，編碼字串時，這三個原始非空格字元會被 QUESTION MARK (U+003F)、DIGIT FIVE (U+0035) 和 DIGIT EIGHT (U+0038) 取代。 DIGIT EIGHT 對於不支援的 INFINITY 字元來說，是相當差的取代，QUESTION MARK 則表示沒有可供原始字元使用的對應。  
  
 [!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
 [!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]  
  
 自動調整對應是 <xref:System.Text.Encoding> 物件的預設行為，可將 Unicode 資料編碼為字碼頁資料，有些舊版應用程式需要這個行為。 不過，基於安全性理由，大多數的新應用程式都應該避免自動調整行為。 例如，應用程式不應該透過自動調整編碼方式放入定義域名稱。  
  
> [!NOTE]
>  您也可以實作編碼的自訂自動調整後援對應。 如需詳細資訊，請參閱 [Implementing a Custom Fallback Strategy](../../../docs/standard/base-types/character-encoding.md#Custom) 一節。  
  
 如果自動調整後援是編碼物件的預設值，則當您藉由呼叫 <xref:System.Text.Encoding> 或 <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> 多載擷取 <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> 物件時，可以選擇其他後援策略。 下一節包含的範例會取代無法使用星號 (*) 對應至字碼頁 1252 的每一個字元。  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
<a name="Replacement"></a>   
### <a name="replacement-fallback"></a>Replacement Fallback  
 當字元在目標配置中沒有完全相符的字元，但是沒有可以對應的適當字元時，應用程式就可以指定取代字元或字串。 這是 Unicode 解碼器的預設行為，該行為會將任何無法解碼的兩個位元組序列取代為 REPLACEMENT_CHARACTER (U+FFFD)。 它也是 <xref:System.Text.ASCIIEncoding> 類別的預設行為，該行為會將任何無法編碼或解碼的每個字元取代為問號。 下列範例說明前一個範例中 Unicode 字串的字元取代。 如輸出所示，每個無法解碼為 ASCII 位元組值的字元都會以 0x3F 取代，也就是以問號取代 ASCII 碼。  
  
 [!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
 [!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]  
  
 .NET 包含 <xref:System.Text.EncoderReplacementFallback> 和 <xref:System.Text.DecoderReplacementFallback> 類別，這兩者會在字元無法於編碼或解碼作業中精確對應時替代取代字串。 根據預設，這個取代字串會是一個問號，但是您可以呼叫類別建構函式多載，以便選擇不同的字串。 取代字串通常 (但不一定) 是單一字元。 下列範例會藉由執行個體化使用星號 (*) 做為取代字串的 <xref:System.Text.EncoderReplacementFallback> 物件，變更字碼頁 1252 編碼器的行為。  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
> [!NOTE]
>  您也可以實作編碼的取代類別。 如需詳細資訊，請參閱 [Implementing a Custom Fallback Strategy](../../../docs/standard/base-types/character-encoding.md#Custom) 一節。  
  
 除了 QUESTION MARK (U+003F) 之外，還常使用 Unicode REPLACEMENT CHARACTER (U+FFFD) 做為取代字串，特別是當解碼無法成功轉譯成 Unicode 字元的位元組序列時。 不過，您可以自由選擇任何取代字串，而且該字串可以包含多個字元。  
  
<a name="Exception"></a>   
### <a name="exception-fallback"></a>Exception Fallback  
 編碼器可在無法編碼一組字元時擲回 <xref:System.Text.EncoderFallbackException> ，而解碼器可在無法解碼位元組陣列時擲回 <xref:System.Text.DecoderFallbackException> ，而不是提供自動調整後援或取代字串。 若要在編碼和解碼作業中擲回例外狀況，請將 <xref:System.Text.EncoderExceptionFallback> 物件和 <xref:System.Text.DecoderExceptionFallback> 物件分別提供給 <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> 方法。 下列範例說明 <xref:System.Text.ASCIIEncoding> 類別的例外狀況後援。  
  
 [!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
 [!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]  
  
> [!NOTE]
>  您也可以實作編碼作業的自訂例外狀況處理常式。 如需詳細資訊，請參閱 [Implementing a Custom Fallback Strategy](../../../docs/standard/base-types/character-encoding.md#Custom) 一節。  
  
 <xref:System.Text.EncoderFallbackException> 和 <xref:System.Text.DecoderFallbackException> 物件提供下列造成例外狀況之條件的相關資訊：  
  
- <xref:System.Text.EncoderFallbackException> 物件包含 <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A> 方法，這個方法會指出無法編碼的一或多個字元代表未知的 Surrogate 字組 (在這種情況下，方法會傳回 `true`)，或未知的單一字元 (在這種情況下，方法會傳回 `false`)。 Surrogate 字組中的字元可從 <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> 和 <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType> 屬性取得。 未知的單一字元可從 <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> 屬性取得。 <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> 屬性會指出字串中找到第一個無法編碼之字元的位置。  
  
- <xref:System.Text.DecoderFallbackException> 物件包含 <xref:System.Text.DecoderFallbackException.BytesUnknown%2A> 屬性，這個屬性會傳回無法解碼的位元組陣列。 <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> 屬性會指出未知位元組的開始位置。  
  
 雖然 <xref:System.Text.EncoderFallbackException> 和 <xref:System.Text.DecoderFallbackException> 物件提供了有關例外狀況的適當診斷資訊，但是並未提供編碼或解碼緩衝區的存取權。 因此，這兩個物件不允許在編碼或解碼方法內取代或更正無效的資料。  
  
<a name="Custom"></a>   
## <a name="implementing-a-custom-fallback-strategy"></a>Implementing a Custom Fallback Strategy  
 除了字碼頁在內部實作的自動調整對應之外，.NET 還包括下列實作後援策略的類別：  
  
- 使用 <xref:System.Text.EncoderReplacementFallback> 和 <xref:System.Text.EncoderReplacementFallbackBuffer> 取代編碼作業中的字元。  
  
- 使用 <xref:System.Text.DecoderReplacementFallback> 和 <xref:System.Text.DecoderReplacementFallbackBuffer> 取代解碼作業中的字元。  
  
- 在無法編碼字元時，使用 <xref:System.Text.EncoderExceptionFallback> 和 <xref:System.Text.EncoderExceptionFallbackBuffer> 擲回 <xref:System.Text.EncoderFallbackException> 。  
  
- 在無法解碼字元時，使用 <xref:System.Text.DecoderExceptionFallback> 和 <xref:System.Text.DecoderExceptionFallbackBuffer> 擲回 <xref:System.Text.DecoderFallbackException> 。  
  
 此外，您可以執行下列步驟，來實作使用自動調整後援、取代後援或例外狀況後援的自訂方案：  
  
1. 針對編碼作業從 <xref:System.Text.EncoderFallback> 衍生類別，並針對解碼作業從 <xref:System.Text.DecoderFallback> 衍生類別。  
  
2. 針對編碼作業從 <xref:System.Text.EncoderFallbackBuffer> 衍生類別，並針對解碼作業從 <xref:System.Text.DecoderFallbackBuffer> 衍生類別。  
  
3. 至於例外狀況後援，如果預先定義的 <xref:System.Text.EncoderFallbackException> 和 <xref:System.Text.DecoderFallbackException> 類別不符合您的需求，則從例外狀況物件 (例如 <xref:System.Exception> 或 <xref:System.ArgumentException>) 衍生類別。  
  
### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>衍生自 EncoderFallback 或 DecoderFallback  
 若要實作自訂後援方案，您必須針對編碼作業建立繼承自 <xref:System.Text.EncoderFallback> 的類別，以及針對解碼作業建立繼承自 <xref:System.Text.DecoderFallback> 的類別。 這些類別的執行個體會傳遞給 <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> 方法，並且做為編碼類別和後援實作之間的媒介。  
  
 當您針對編碼器或解碼器建立自訂後援方案時，必須實作下列成員：  
  
- <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> 或 <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType> 屬性，這個屬性會傳回自動調整、取代或例外狀況後援可傳回以取代單一字元的最大字元數。 若是自訂例外狀況後援，其值為零。  
  
- <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> 或 <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> 方法，這個方法會傳回您自訂的 <xref:System.Text.EncoderFallbackBuffer> 或 <xref:System.Text.DecoderFallbackBuffer> 實作。 編碼器會在遇到無法成功編碼的第一個字元時呼叫這個方法，而解碼器會在遇到無法成功解碼的第一個位元組時呼叫這個方法。  
  
### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>衍生自 EncoderFallbackBuffer 或 DecoderFallbackBuffer  
 若要實作自訂後援方案，您還必須針對編碼作業建立繼承自 <xref:System.Text.EncoderFallbackBuffer> 的類別，以及針對解碼作業建立繼承自 <xref:System.Text.DecoderFallbackBuffer> 的類別。 這些類別的執行個體會由 <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> 和 <xref:System.Text.EncoderFallback> 類別的 <xref:System.Text.DecoderFallback> 方法傳回。 編碼器會在遇到無法編碼的第一個字元時呼叫 <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> 方法，而解碼器會在遇到無法解碼的一或多個位元組時呼叫 <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> 方法。 <xref:System.Text.EncoderFallbackBuffer> 和 <xref:System.Text.DecoderFallbackBuffer> 類別提供後援實作。 每個執行個體代表包含後援字元的緩衝區，這些後援字元將取代無法編碼的字元或無法解碼的位元組序列。  
  
 當您針對編碼器或解碼器建立自訂後援方案時，必須實作下列成員：  
  
- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 或 <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 方法。 編碼器會呼叫<xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 來提供後援緩衝區，其中包含無法編碼之字元的相關資訊。 由於要編碼的字元可能是 Surrogate 字組，因此這個方法為多載。 其中一個多載會收到傳遞之要編碼的字元，以及其在字串中的索引。 第二個多載會收到傳遞的高和低 Surrogate，以及其在字串中的索引。 解碼器會呼叫 <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> 方法來提供後援緩衝區，其中包含無法解碼之位元組的相關資訊。 這個方法會收到傳遞之無法解碼的位元組陣列，以及第一個位元組的索引。 如果後援緩衝區可以提供自動調整或一或多個取代字元，則後援方法應該傳回 `true` ，否則應該傳回 `false`。 若是例外狀況後援，後援方法應該擲回例外狀況。  
  
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> 或 <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> 方法，編碼器或解碼器會重複呼叫這個方法，以便從後援緩衝區取得下一個字元。 當所有後援字元都已傳回時，這個方法應傳回 U+0000。  
  
- <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> 或 <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> 屬性，這個屬性會傳回後援緩衝區中剩餘的字元數。  
  
- <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> 或 <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> 方法，這個方法會將後援緩衝區中的目前位置移至前一個字元。  
  
- <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> 或 <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> 方法，這個方法會重新初始化後援緩衝區。  
  
 如果後援實作是自動調整後援或取代後援，則衍生自 <xref:System.Text.EncoderFallbackBuffer> 和 <xref:System.Text.DecoderFallbackBuffer> 的類別還會維護兩個私用執行個體欄位：緩衝區中確實的字元數，以及緩衝區中要傳回之下一個字元的索引。  
  
### <a name="an-encoderfallback-example"></a>EncoderFallback 範例  
 之前的範例使用取代後援來取代未對應至包含星號 (*) 之 ASCII 字元的 Unicode 字元。 下列範例使用自訂自動調整後援實作，而不是提供較佳的非 ASCII 字元對應。  
  
 下列程式碼會定義名為 `CustomMapper` 的類別，該類別衍生自 <xref:System.Text.EncoderFallback> ，會處理非 ASCII 字元的自動調整對應。 其 `CreateFallbackBuffer` 方法會傳回提供 `CustomMapperFallbackBuffer` 實作的 <xref:System.Text.EncoderFallbackBuffer> 物件。 `CustomMapper` 類別使用 <xref:System.Collections.Generic.Dictionary%602> 物件來儲存不支援的 Unicode 字元對應 (機碼值) 及其對應的 8 位元字元 (儲存在 64 位元整數的兩個連續的位元組中)。 為了讓後援緩衝區可以使用這項對應， `CustomMapper` 執行個體會當做參數傳遞給 `CustomMapperFallbackBuffer` 類別建構函式。 由於最長的對應是代表 Unicode 字元 U+221E 的字串 "INF"，因此 `MaxCharCount` 屬性會傳回 3。  
  
 [!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
 [!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]  
  
 下列程式碼會定義 `CustomMapperFallbackBuffer` 類別，該類別衍生自 <xref:System.Text.EncoderFallbackBuffer>。 包含自動調整對應並在 `CustomMapper` 執行個體中定義的字典可從其類別建構函式取得。 如果 ASCII 編碼器無法編碼的任何 Unicode 字元是在對應字典中定義，則其 `Fallback` 方法會傳回 `true` ，否則會傳回 `false`。 針對每個後援，私用 `count` 變數會指出要傳回的剩餘字元數，而私用 `index` 變數會指出要傳回的下一個字元在字串緩衝區 `charsToReturn`中的位置。  
  
 [!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
 [!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]  
  
 接著，下列程式碼會執行個體化 `CustomMapper` 物件，並將該物件的執行個體傳遞給 <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> 方法。 輸出會指出，自動調整後援實作成功處理原始字串中這三個非 ASCII 字元。  
  
 [!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
 [!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Text.Encoder>
- <xref:System.Text.Decoder>
- <xref:System.Text.DecoderFallback>
- <xref:System.Text.Encoding>
- <xref:System.Text.EncoderFallback>
- [全球化和當地語系化](../../../docs/standard/globalization-localization/index.md)
