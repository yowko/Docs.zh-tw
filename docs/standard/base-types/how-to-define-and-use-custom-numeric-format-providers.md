---
title: "如何：定義和使用自訂數值格式提供者"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- custom numeric format strings
- numbers [.NET Framework], custom numeric format strings
- displaying date and time data
- format providers [.NET Framework]
- custom format strings
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e44a909eb92f0d9dfa21980a918a2d370dcf427
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>如何：定義和使用自訂數值格式提供者
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]可讓您廣泛控制數值的字串表示。 它支援以下自訂數值格式的功能：  
  
-   標準數值格式字串，這些字串提供預先定義的格式集，可將數字轉換成其字串表示。 您可以使用任何數字格式化方法，例如<xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>，具有`format`參數。 如需詳細資訊，請參閱[標準數值格式字串](../../../docs/standard/base-types/standard-numeric-format-strings.md)。  
  
-   自訂數值格式字串，這些字串提供能夠合併的符號集，可用來定義自訂數值格式規範。 也可以使用以例如格式化方法的任何數字<xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>，具有`format`參數。 如需詳細資訊，請參閱[自訂數值格式字串](../../../docs/standard/base-types/custom-numeric-format-strings.md)。  
  
-   自訂<xref:System.Globalization.CultureInfo>或<xref:System.Globalization.NumberFormatInfo>物件定義的符號和格式顯示數值的字串表示所使用的模式。 您可以使用任何數字格式化方法，例如<xref:System.Int32.ToString%2A>，具有`provider`參數。 一般而言，`provider`參數用來指定特定文化特性的格式。  
  
 在某些情況下，這三項技術並不適用 (例如，應用程式必須顯示格式化帳號、身分證號碼或是郵遞區號時)。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]也可讓您定義既不是其格式化物件<xref:System.Globalization.CultureInfo>也未<xref:System.Globalization.NumberFormatInfo>物件，以判斷如何格式化數字的值。 本主題提供實作這類物件的逐步指示，並提供格式化電話號碼的範例。  
  
### <a name="to-define-a-custom-format-provider"></a>定義自訂格式提供者  
  
1.  定義類別可實作<xref:System.IFormatProvider>和<xref:System.ICustomFormatter>介面。  
  
2.  實作 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> 方法。 <xref:System.IFormatProvider.GetFormat%2A>是一種回呼方法，則格式化方法 (例如<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>方法) 叫用以擷取負責實際執行的自訂格式的物件。 典型實作<xref:System.IFormatProvider.GetFormat%2A>會進行下列作業：  
  
    1.  決定是否<xref:System.Type>物件傳遞為方法參數代表<xref:System.ICustomFormatter>介面。  
  
    2.  如果參數代表<xref:System.ICustomFormatter>介面，<xref:System.IFormatProvider.GetFormat%2A>傳回該物件會實作<xref:System.ICustomFormatter>負責提供自訂格式的介面。 一般而言，自訂格式物件會自行傳回。  
  
    3.  如果參數不代表<xref:System.ICustomFormatter>介面，<xref:System.IFormatProvider.GetFormat%2A>傳回`null`。  
  
3.  實作 <xref:System.ICustomFormatter.Format%2A> 方法。 這個方法會呼叫<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>方法，並負責傳回數字的字串表示。 實作這個方法通常包含下列各項：  
  
    1.  （選擇性） 確認，方法合法為了提供格式化服務藉由檢查`provider`參數。 用來格式化物件的同時實作<xref:System.IFormatProvider>和<xref:System.ICustomFormatter>，這牽涉到測試`provider`參數與目前的格式物件是否相等。  
  
    2.  決定格式物件是否應支援自訂格式規範 (例如，"N" 格式規範可能表示應使用 NANP 格式輸出美國電話號碼，而 "I" 可能表示使用 ITU-T Recommendation E.123 格式輸出)。如果使用格式規範，則這個方法應處理特定格式規範。 它會傳遞至方法中`format`參數。 如果沒有規範存在，值`format`參數是<xref:System.String.Empty?displayProperty=nameWithType>。  
  
    3.  擷取數值的值傳遞給方法的`arg`參數。 執行任何必要的操作，將它轉換成其字串表示。  
  
    4.  傳回的字串表示法`arg`參數。  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>使用自訂數值格式物件  
  
1.  建立自訂格式類別的新執行個體。  
  
2.  呼叫<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>格式方法，將其傳遞自訂格式化物件的格式規範 (或<xref:System.String.Empty?displayProperty=nameWithType>，如果不使用其中一種)，以及要格式化的數值。  
  
## <a name="example"></a>範例  
 下列範例會定義名為 `TelephoneFormatter` 的自訂數值格式提供者，它會將代表美國電話號碼的數字轉換成 NANP 或 E.123 格式。 這個方法會處理兩種格式規範："N" (輸出 NANP 格式) 和 "I" (輸出國際 E.123 格式)。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 自訂數值格式提供者可以只用於<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>方法。 其他多載的格式化方法的數字 (例如`ToString`) 具有類型的參數<xref:System.IFormatProvider>通過所有<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>實作<xref:System.Type>物件，代表<xref:System.Globalization.NumberFormatInfo>型別。 傳回，他們期望應用程式方法來傳回<xref:System.Globalization.NumberFormatInfo>物件。 如果不存在，則會略過自訂數值格式提供者，而<xref:System.Globalization.NumberFormatInfo>物件目前的文化特性會使用其所在位置。 在範例中，`TelephoneFormatter.GetFormat`方法會處理它可能不適當地傳遞至格式方法，藉由檢查方法參數，並傳回數值的可能性`null`如果它代表類型以外<xref:System.ICustomFormatter>。  
  
 如果自訂數值格式提供者支援一組的格式規範，請確定您提供的預設行為，如果沒有格式規範中使用的格式項目中提供<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>方法呼叫。 在此範例中，"N" 是預設的格式規範。 如此即可提供明確格式規範，將數字轉換成格式化的電話號碼。 下列範例說明這類方法呼叫。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 不過，它也允許在沒有格式規範的情況下進行轉換。 下列範例說明這類方法呼叫。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 如果未不定義任何預設的格式規範，則您的實作<xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType>方法應該包含如下所示的程式碼，讓該.NET 提供格式化您的程式碼不支援。  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 在此範例中，該方法的實作<xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType>旨在做為回呼方法，以便<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>方法。 因此，它會檢查`formatProvider`參數，來判斷它是否包含目前的參考`TelephoneFormatter`物件。 不過，此方法也可以直接從程式碼呼叫。 在此情況下，您可以使用`formatProvider`參數，以提供<xref:System.Globalization.CultureInfo>或<xref:System.Globalization.NumberFormatInfo>物件，提供特定文化特性格式資訊。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 在命令列使用 csc.exe 或 vb.exe 程式碼編譯。 若要編譯中的程式碼[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]，將其放在主控台應用程式專案範本。  
  
## <a name="see-also"></a>另請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)
