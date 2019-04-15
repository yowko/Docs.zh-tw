---
title: 開發世界性的應用程式的最佳作法
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d96e223b85178c7f2784a523e5609057d1432488
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310534"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>開發世界性應用程式的最佳做法

本章節將說明開發世界性的應用程式的最佳作法。

## <a name="globalization-best-practices"></a>全球化最佳做法

1. 請在內部製作您的應用程式 Unicode。

2. 使用 <xref:System.Globalization> 命名空間提供的文化特性感知類別來管理和格式化資料。

    - 如需排序，請使用 <xref:System.Globalization.SortKey> 類別和 <xref:System.Globalization.CompareInfo> 類別。

    - 如需字串比較，請使用 <xref:System.Globalization.CompareInfo> 類別。

    - 如需日期和時間格式化，請使用 <xref:System.Globalization.DateTimeFormatInfo> 類別。

    - 如需數字格式化，請使用 <xref:System.Globalization.NumberFormatInfo> 類別。

    - 對於西曆和非西曆，請使用 <xref:System.Globalization.Calendar> 類別或其中一個特定曆法實作。

3. 在適當情況下使用 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> 類別提供的文化特性屬性設定。 使用 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 屬性來格式化工作，例如日期和時間或數字格式化。 使用 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 屬性來擷取資源。 請注意，您可以根據個別執行緒來設定 `CurrentCulture` 和 `CurrentUICulture` 屬性。

4. 啟用您的應用程式使用 <xref:System.Text> 命名空間中的編碼類別來回讀取和寫入各種編碼方式的資料。 請勿假設 ASCII 資料。 請假設在使用中輸入文字的地方提供國際字元。 例如，應用程式應該會接受在伺服器名稱、目錄、檔名和 URL 中使用國際字元。

5. 在使用 <xref:System.Text.UTF8Encoding> 類別時，基於安全理由，請使用這個類別所提供的錯誤偵測功能。 若要開啟錯誤偵測功能，請使用採用 `throwOnInvalidBytes` 參數的建構函式，並將此參數的值設定為 `true`，以建立此類別的執行個體。

6. 如果可能的話，請將字串當做完整的字串處理，而不是連續的個別字串。 在排序或搜尋子字串時，這點特別重要。 它將可避免發生剖析組合字元的相關問題。 您也可利用 <xref:System.Globalization.StringInfo?displayProperty=nameWithType> 類別，便無須使用單一字元，而是以單位來使用文字。

7. 使用 <xref:System.Drawing> 命名空間提供類別來顯示文字。

8. 為了作業系統的一致性，請勿使用使用者設定來覆寫 <xref:System.Globalization.CultureInfo>。 請使用採用 `CultureInfo` 參數的 `useUserOverride` 建構函式，並將此參數設定為 `false`。

9. 使用國際資料，在國際作業系統版本上測試您的應用程式功能。

10. 如果安全性決策是根據字串比較或大小寫變更作業的結果而定，則請使用不區分文化特性 (Culture) 的字串作業。 這種作法可以確保結果不會受 `CultureInfo.CurrentCulture` 的值所影響。 如需示範區分文化特性 (Culture) 的字串比較如何產生不一致結果的範例，請參閱[使用字串的最佳做法](../../../docs/standard/base-types/best-practices-strings.md)中的[「使用目前文化特性 (Culture) 的字串比較」](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture)一節。

## <a name="localization-best-practices"></a>當地語系化最佳做法

1. 將所有可當地語系化資源移到個別僅含資源的 DLL。 可當地語系化的資源包括使用者介面項目，例如字串、錯誤訊息、對話方塊、功能表和內嵌物件資源。

2. 請勿將字串或使用者介面資源寫在程式中。

3. 請勿將不可當地語系化的資源放入僅含資源的 DLL。 它將造成轉譯器的混淆。

4. 請勿使用在執行階段建置和來自連結字詞的複合字串。 複合字串很難進行當地語系化，因為它們通常會使用不適用於所有語言的英文文法順序。

5. 避免模糊的建構，例如 "Empty Folder"，其中的字串將依據字串元件擔任的文法角色，而進行不同的轉譯。 例如，"empty" 可以是動詞或形容詞，在某些語言中會有不同的轉譯結果，例如義大利文或法文。

6. 避免在您的應用程式中使用含有文字的影像和圖示。 它們進行當地語系化的成本過高。

7. 請保留充分的空間，以便在應用程式介面中擴展字串長度。 在某些語言中，字詞所需要的空間可能比在其他語言多百分之 50-75。

8. 使用 <xref:System.Resources.ResourceManager?displayProperty=nameWithType> 類別來根據文化特性擷取資源。

9. 使用 [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 建立 [Windows Forms] 對話方塊，如此就能使用 [Windows Forms 資源編輯器 (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md) 將對話方塊當地語系化。 請不要以手動方式編碼 Windows Form 對話方塊。

10. 進行專業當地語系化 (轉譯)。

11. 如需建立和當地語系化資源的完整描述，請參閱[應用程式中的資源](../../../docs/framework/resources/index.md)。

## <a name="globalization-best-practices-for-aspnet-applications"></a>ASP.NET 應用程式的全球化最佳做法

1. 在應用程式中明確設定 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> 和 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> 屬性。 請勿過於依賴預設值。

2. 請注意，ASP.NET 應用程式是 Managed 應用程式，因此可使用和其他 Managed 應用程式相同的類別，根據文化特性來擷取、顯示和管理資訊。

3. 請注意，您可以指定下列三種 ASP.NET 中的編法方式類型：

    - requestEncoding 指定從用戶端瀏覽器接收的編法方式。

    - responseEncoding 指定要傳送到用戶端瀏覽器的編碼方式。 在多數情況下，此編碼方式應該與 requestEncoding 指定的編碼方式相同。

    - fileEncoding 指定 .aspx、.asmx 和 .asax 檔案剖析的預設編碼方式。

4. 指定 ASP.NET 應用程式中，下列三個位置的 requestEncoding、responseEncoding、fileEncoding、culture 和 uiCulture 屬性值：

    - 在 Web.config 檔案的全球化區段中。 這個程式位於 ASP.NET 應用程式外部。 如需詳細資訊，請參閱 [\<globalization> 元素](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100))。

    - 在網頁指示詞中。 請注意，當應用程式位於網頁中，表示這個檔案已被讀取。 因此，此時要指定 fileEncoding 和 requestEncoding 已經太遲了。 您只能在網頁指示詞中指定 uiCulture、Culture 和 responseEncoding。

    - 應用程式的程式碼。 這個設定會根據個別要求而有所不同。 和網頁指示詞一樣，使用應用程式碼時，表示要指定 fileEncoding 和 requestEncoding 已經太遲了。 您只能在應用程式碼中指定 uiCulture、Culture 和 responseEncoding。

5. 請注意，uiCulture 值可設為瀏覽器所接受的語言。

## <a name="see-also"></a>另請參閱

- [全球化和當地語系化](../../../docs/standard/globalization-localization/index.md)
- [桌面應用程式中的資源](../../../docs/framework/resources/index.md)
