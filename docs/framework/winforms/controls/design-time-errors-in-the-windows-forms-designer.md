---
title: Windows Form 設計工具中的設計階段錯誤
ms.date: 09/09/2019
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 96ec50e5d3aca2aa24d68d565a35ec7687df2a2e
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893263"
---
# <a name="windows-forms-designer-error-page"></a>Windows Form 設計工具錯誤頁面

如果 Windows Form 設計工具因程式碼中的錯誤、協力廠商元件或其他位置而無法載入時，您會看到錯誤頁面，而不是設計工具。 這個錯誤頁面不一定表示設計工具中有錯誤。 錯誤可能是程式碼後置頁面中的某處，其\<名稱為 > 的格式。Designer.cs。 錯誤會出現在可折迭的黃色列中，並有連結可以跳到字碼頁上錯誤的位置。

![Windows Form 設計工具錯誤頁面](media/windows-forms-designer-error-page-collapsed.png)

您可以選擇忽略錯誤，並按一下 [**略過並繼續**] 繼續載入設計工具。 此動作可能會導致非預期的行為，例如，控制項可能不會出現在設計介面上。

## <a name="instances-of-this-error"></a>此錯誤的實例

擴充黃色的誤差線時，會列出錯誤的每個實例。 許多錯誤類型包含以下列格式呈現的確切位置： *[專案名稱]* *[表單名稱]* 行： *[行號]* 欄： *[欄號]* 。 如果呼叫堆疊與錯誤相關聯，您可以按一下 [**顯示呼叫堆疊**] 連結來查看它。 檢查呼叫堆疊可進一步協助您解決此錯誤。

![Windows Form 設計工具展開的錯誤](media/windows-forms-designer-error-page-expanded.png)

> [!NOTE]
> - 針對 Visual Basic 應用程式，設計階段錯誤頁面不會顯示一個以上的錯誤，但可能會顯示多個相同錯誤的實例。
> - 若C++為應用程式，錯誤不具有程式碼位置連結。

## <a name="help-with-this-error"></a>關於此錯誤的說明

如果有可用錯誤的說明主題，請按一下 [ **MSDN**說明] 連結，直接流覽至 docs.microsoft.com 上的 [說明] 頁面。

## <a name="forum-posts-about-this-error"></a>此錯誤的相關論壇文章

按一下**MSDN 論壇，尋找與此錯誤連結相關的文章**，以流覽至 Microsoft 開發人員網路論壇。 您可能想要特別搜尋[Windows Form 設計工具](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)或[Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)論壇。

## <a name="design-time-errors"></a>設計階段錯誤

本節列出您可能會遇到的一些錯誤。

### <a name="identifier-name-is-not-a-valid-identifier"></a>'\<識別碼名稱 > ' 不是有效的識別碼

此錯誤表示欄位、方法、事件或物件的名稱不正確。

### <a name="name-already-exists-in-project-name"></a>' name > ' 已存在 '\<專案名稱 > ' 中\<

錯誤訊息：「'\<name > ' 已經存在 '\<project name > ' 中。 請輸入唯一的名稱。」

您已為專案中已經存在的繼承表單指定名稱。 若要更正此錯誤，請為繼承的表單指定唯一的名稱。

### <a name="toolbox-tab-name-is-not-a-toolbox-category"></a>[\<工具箱] 索引標籤名稱 > ' 不是工具箱分類

協力廠商設計人員嘗試存取 [工具箱] 上不存在的索引標籤。 請洽詢元件廠商。

### <a name="a-requested-language-parser-is-not-installed"></a>未安裝要求的語言剖析器

錯誤訊息：「未安裝要求的語言剖析器。 語言剖析器名稱為 '{0}'。」

Visual Studio 嘗試載入已註冊檔案類型但無法執行的設計工具。 這很可能是因為在安裝期間發生錯誤。 請洽詢您要用來修正的語言廠商。

### <a name="a-service-required-for-generating-and-parsing-source-code-is-missing"></a>遺失產生及剖析原始程式碼所必備的服務

這是協力廠商元件的問題。 請洽詢元件廠商。

### <a name="an-exception-occurred-while-trying-to-create-an-instance-of-object-name"></a>嘗試建立 '\<object name > ' 的實例時發生例外狀況

錯誤訊息：「嘗試建立 '\<object name > ' 的實例時發生例外狀況。 例外狀況是\<「例外狀況\>字串」。

協力廠商設計師要求 Visual Studio 建立物件，但物件引發錯誤。 請洽詢元件廠商。

### <a name="another-editor-has-document-name-open-in-an-incompatible-mode"></a>另一個編輯器\<在不相容的模式下開啟 [檔案名稱 >]

錯誤訊息：「另一個編輯器在\<不相容的模式下開啟了「檔案名稱 >」。 請關閉編輯器，然後再次嘗試此操作。」

如果您嘗試開啟已在另一個編輯器中開啟的檔案，就會發生這個錯誤。 隨即顯示已開啟檔案的編輯器。 若要更正這個錯誤，請關閉已開啟檔案的編輯器，然後再試一次。

### <a name="another-editor-has-made-changes-to-document-name"></a>另一個編輯器已變更\<「檔案名稱 >」

關閉並重新開啟設計工具，變更才會生效。 一般來說，Visual Studio 在進行變更之後，會自動重載設計工具。 不過，其他設計工具（例如協力廠商元件設計工具）可能不支援重載行為。 在此情況下，Visual Studio 會提示您手動關閉並重新開啟設計工具。

### <a name="another-editor-has-the-file-open-in-an-incompatible-mode"></a>另一個編輯器在不相容的模式下開啟檔案

錯誤訊息：「另一個編輯器在不相容的模式下開啟檔案。 請關閉編輯器，然後再次嘗試此操作。」

此訊息類似于「另一個編輯器\<在不相容的模式中開啟 >」，但 Visual Studio 無法判斷檔案名。 若要更正這個錯誤，請關閉已開啟檔案的編輯器，然後再試一次。

### <a name="array-rank-rank-in-array-is-too-high"></a>陣列次序 '\<陣列中的順位 > ' 太高

Visual Studio 只支援設計工具剖析之程式碼區塊中的單一維度陣列。 多維陣列在此區域外有效。

### <a name="assembly-assembly-name-could-not-be-opened"></a>無法開啟\<元件 ' assembly name > '

錯誤訊息：無法開啟「\<元件」元件名稱 > '。 請確認檔案仍然存在。」

當您嘗試開啟無法開啟的檔案時，就會出現這個錯誤訊息。 請確認檔案存在，而且是有效的元件。

### <a name="bad-element-type-this-serializer-expects-an-element-of-type-type-name"></a>不正確的元素類型。 此序列化程式需要類型 '\<type name > ' 的元素

這是協力廠商元件的問題。 請洽詢元件廠商。

### <a name="cannot-access-the-visual-studio-toolbox-at-this-time"></a>目前無法存取 Visual Studio 工具箱

Visual Studio 對 [工具箱] 進行呼叫，這是無法使用的。 如果您看到此錯誤，如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。

### <a name="cannot-bind-an-event-handler-to-the-event-name-event-because-it-is-read-only"></a>無法將事件處理常式系結至\<' event name > ' 事件，因為它是唯讀的

當您嘗試將事件連接至繼承自基類的控制項時，通常會發生這個錯誤。 如果控制項的成員變數為私用，Visual Studio 無法將事件連接至方法。 私下繼承的控制項不能有其他系結的事件。

### <a name="cannot-create-a-method-name-for-the-requested-component-because-it-is-not-a-member-of-the-design-container"></a>因為要求的元件不是設計容器的成員，所以無法建立方法名稱

Visual Studio 嘗試將事件處理常式加入至設計工具中沒有成員變數的元件。 請洽詢元件廠商。

### <a name="cannot-name-the-object-name-because-it-is-already-named-name"></a>無法命名物件 '\<name > '，因為它已經命名為 '\<name > '

這是 Visual Studio 序列化程式中的內部錯誤。 這表示序列化程式嘗試將物件命名為兩次，這是不支援的。 如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。

### <a name="cannot-remove-or-destroy-inherited-component-component-name"></a>無法移除或摧毀繼承的元件\<' component name > '

繼承的控制項在繼承類別的擁有權之下。 繼承控制項的變更必須在控制項來源的類別中進行。 因此，您無法將它重新命名或摧毀。

### <a name="category-toolbox-tab-name-does-not-have-a-tool-for-class-class-name"></a>分類的 [\<工具箱]索引標籤名稱>'沒有類別「類別名稱\<>」的工具

設計工具嘗試參考特定 [工具箱] 索引標籤上的類別，但該類別不存在。 請洽詢元件廠商。

### <a name="class-class-name-has-no-matching-constructor"></a>類別 '\<class name > ' 沒有相符的函式

協力廠商的設計工具要求 Visual Studio 在不存在的函式中，以特定參數建立物件。 請洽詢元件廠商。

### <a name="code-generation-for-property-property-name-failed"></a>屬性 '\<屬性名稱 > ' 的程式碼產生失敗

這是錯誤的泛型包裝函式。 此訊息隨附的錯誤字串將提供有關錯誤訊息的更多詳細資料，並具有更特定說明主題的連結。 若要更正此錯誤，請解決錯誤訊息中所指定的錯誤，此錯誤會附加到此錯誤。

### <a name="component-component-name-did-not-call-containeradd-in-its-constructor"></a>元件的\<元件名稱 > ' 未在其函式中呼叫 Container. Add （）

這是您剛載入或置於表單上的元件中的錯誤。 這表示元件並未將本身新增至其容器控制項（不論是另一個控制項或表單）。 設計工具會繼續運作，但元件可能會在執行時間發生問題。

若要更正錯誤，請洽詢元件廠商。 或者，如果它是您所建立的元件，請`IContainer.Add`在元件的「函式」中呼叫方法。

### <a name="component-name-cannot-be-empty"></a>元件名稱不可為空白

當您嘗試將元件重新命名為空值時，就會發生此錯誤。

### <a name="could-not-access-the-variable-variable-name-because-it-has-not-been-initialized-yet"></a>無法存取變數\<的變數名稱 > '，因為它尚未初始化

發生此錯誤的原因有兩個。 協力廠商元件廠商的控制項或元件已散發，或是您所撰寫的程式碼在元件之間具有遞迴相依性時，可能會有問題。

若要更正這個錯誤，請確定您的程式碼沒有遞迴相依性。 如果沒有這類問題，請注意錯誤訊息的確切文字，並與元件廠商聯繫。

### <a name="could-not-find-type-type-name"></a>找不到類型 '\<type name > '

錯誤訊息：「找不到類型\<名稱 > '。 請確定已參考包含此類型的元件。 如果這種類型是您開發專案的一部分，請確定已成功建立專案。」

發生此錯誤的原因是找不到參考。 請確定已參考錯誤訊息中所指出的類型，而且也會參考該類型所需的任何元件。 問題通常是，尚未建立解決方案中的控制項。 若要建立，請從 [**建立**] 功能表中選取 [**建立方案**]。 否則，如果已經建立控制項，請從方案總管中 [**參考**] 或 [相依性 **]** 資料夾的右鍵功能表中，手動加入參考。

### <a name="could-not-load-type-type-name"></a>無法載入類型 '\<type name > '

錯誤訊息：「無法載入類型 '\<類型名稱 > '。 請確定包含此類型的元件已加入至專案參考。」

Visual Studio 嘗試連接事件處理方法，但找不到方法的一或多個參數類型。 這通常是因為遺漏參考所造成。 若要更正這個錯誤，請將包含該類型的參考新增至專案，然後再試一次。

### <a name="could-not-locate-the-project-item-templates-for-inherited-components"></a>找不到繼承元件的專案項目範本

Visual Studio 中的繼承表單的範本無法使用。 如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。

### <a name="delegate-class-class-name-has-no-invoke-method-is-this-class-a-delegate"></a>委派類別 '\<class name > ' 沒有 invoke 方法。 這個類別是委派嗎？

Visual Studio 嘗試建立事件處理常式，但事件種類發生錯誤。 如果事件是由不符合 CLS 標準的語言所建立，則會發生這種情況。 請洽詢元件廠商。

### <a name="duplicate-declaration-of-member-member-name"></a>成員 '\<member name > ' 的重複宣告

發生此錯誤的原因是成員變數已宣告兩次（例如，在程式碼`Button1`中宣告了兩個名為的控制項）。 名稱在繼承的表單中必須是唯一的。 此外，名稱不能只有大小寫不同。

### <a name="error-reading-resources-from-the-resource-file-for-the-culture-culture-name"></a>從資源檔讀取文化特性 '\<文化特性名稱 > ' 的資源時發生錯誤

如果專案中有錯誤的 .resx 檔案，就會發生這個錯誤。

若要更正此錯誤：

1. 按一下 方案總管中的 **顯示所有**檔案 按鈕，以查看與方案相關聯的 .resx 檔案。
2. 在 XML 編輯器中載入 .resx 檔案，方法是以滑鼠右鍵按一下 .resx 檔案，然後選擇 [**開啟**]。
3. 手動編輯 .resx 檔案以解決錯誤。

### <a name="error-reading-resources-from-the-resource-file-for-the-default-culture-culture-name"></a>從資源檔讀取預設文化\<特性名稱 > ' 的資源時發生錯誤

如果專案中有不正確的 .resx 檔案作為預設文化特性，就會發生這個錯誤。

若要更正此錯誤：

1. 按一下 方案總管中的 **顯示所有**檔案 按鈕，以查看與方案相關聯的 .resx 檔案。
2. 在 XML 編輯器中載入 .resx 檔案，方法是以滑鼠右鍵按一下 .resx 檔案，然後選擇 [**開啟**]。
3. 手動編輯 .resx 檔案以解決錯誤。

### <a name="failed-to-parse-method-method-name"></a>無法剖析方法 '\<method name > '

錯誤訊息：「無法剖析方法 '\<方法名稱 > '。 剖析器回報下列錯誤：\<「錯誤字串 >」。 請查看工作清單中是否有潛在的錯誤。」

這是在剖析期間所發生之問題的一般錯誤訊息。 這些錯誤通常是因為語法錯誤所造成。 如需與錯誤相關的特定訊息，請參閱工作清單。

### <a name="invalid-component-name-component-name"></a>不正確元件名稱：\<' 元件名稱 > '

您已嘗試將元件重新命名為該語言的無效值。 若要更正此錯誤，請為元件命名，使其符合該語言的命名規則。

### <a name="the-type-class-name-is-made-of-several-partial-classes-in-the-same-file"></a>類型 '\<class name > ' 是由相同檔案中的數個部分類別所組成

當您使用[partial](/dotnet/csharp/language-reference/keywords/partial-type)關鍵字在多個檔案中定義類別時，每個檔案中只能有一個部分定義。

若要更正這個錯誤，請從檔案中移除類別的所有部分定義，而不是全部。

### <a name="the-assembly-assembly-name-could-not-be-found"></a>找不到\<元件 ' assembly name > '

錯誤訊息：找不到「\<元件」元件名稱 > '。 請確定已參考此元件。 如果元件是目前開發專案的一部分，請確定已建立專案。」

此錯誤類似「找不到類型 '\<類型名稱 > '」，但通常是因為中繼資料屬性而發生此錯誤。 若要更正這個錯誤，請檢查屬性所使用的所有元件都已被參考。

### <a name="the-assembly-name-assembly-name-is-invalid"></a>元件名稱 '\<assembly name > ' 無效

元件已要求特定的元件，但元件提供的名稱不是有效的元件名稱。 請洽詢元件廠商。

### <a name="the-base-class-class-name-cannot-be-designed"></a>無法設計基類 '\<class name > '

Visual Studio 載入類別，但無法設計類別，因為類別的實施者並未提供設計工具。 如果類別支援設計工具，請確定沒有任何問題會導致在設計工具（例如編譯器錯誤）中顯示問題。 此外，請確定對類別的所有參考都是正確的，而且所有類別名稱的拼寫正確。 否則，如果類別無法設計，請在程式碼視圖中進行編輯。

### <a name="the-base-class-class-name-could-not-be-loaded"></a>無法載入基類 '\<class name > '

專案中未參考類別，因此 Visual Studio 無法載入。 若要更正這個錯誤，請將參考新增至專案中的類別，然後關閉並重新開啟 [Windows Form 設計工具] 視窗。

### <a name="the-class-class-name-cannot-be-designed-in-this-version-of-visual-studio"></a>無法在這個\<版本的中設計類別的類別名稱 > ' Visual Studio

這個控制項或元件的設計工具不支援與 Visual Studio 相同的類型。 請洽詢元件廠商。

### <a name="the-class-name-is-not-a-valid-identifier-for-this-language"></a>類別名稱不是此語言的有效識別項

使用者所建立的原始程式碼具有類別名稱，對所使用的語言無效。 若要更正此錯誤，請將類別命名為符合語言需求。

### <a name="the-component-cannot-be-added-because-it-contains-a-circular-reference-to-reference-name"></a>無法加入元件，因為它包含 '\<reference name > ' 的迴圈參考

您不能將控制項或元件新增至本身。 發生這種情況的另一種情況是，如果表單的 InitializeComponent 方法中有程式碼（例如 Form1），則會建立另一個 Form1 的實例。

### <a name="the-designer-cannot-be-modified-at-this-time"></a>目前無法修改設計工具

當編輯器中的檔案標示為唯讀時，就會發生這個錯誤。 請確定檔案未標示為唯讀，且應用程式未執行。

### <a name="the-designer-could-not-be-shown-for-this-file-because-none-of-the-classes-within-it-can-be-designed"></a>無法對這個檔案顯示設計工具，因為檔案中沒有可以設計的類別

當 Visual Studio 找不到滿足設計工具需求的基類時，就會發生這個錯誤。 表單和控制項必須衍生自支援設計工具的基類。 如果您是從繼承的表單或控制項衍生，請確定已建立專案。

### <a name="the-designer-for-base-class-class-name-is-not-installed"></a>未安裝基類\<「類別名稱 >」的設計工具

Visual Studio 無法載入類別的設計工具。 如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。

### <a name="the-designer-must-create-an-instance-of-type-type-name-but-it-cant-because-the-type-is-declared-as-abstract"></a>設計工具必須建立類型 '\<type name > ' 的實例，但因為該類型宣告為抽象，所以無法這麼做

發生這個錯誤的原因是，傳遞至設計工具之物件的基類是[抽象](/dotnet/csharp/language-reference/keywords/abstract)的，這是不允許的。

### <a name="the-file-could-not-be-loaded-in-the-designer"></a>設計工具無法載入檔案

這個檔案的基類不支援任何設計工具。 因應措施是使用程式碼 view 來處理檔案。 以滑鼠右鍵按一下方案總管中的檔案，然後選擇 [ **View Code**]。

### <a name="the-language-for-this-file-does-not-support-the-necessary-code-parsing-and-generation-services"></a>這個檔案所使用的語言不支援必要的程式碼剖析與產生服務

錯誤訊息：「此檔案的語言不支援必要的程式碼剖析和產生服務。 請確定您要開啟的檔案是專案的成員，然後再次嘗試開啟檔案。」

這個錯誤最可能是因為在不支援設計工具的專案中開啟檔案所造成。

### <a name="the-language-parser-class-class-name-is-not-implemented-properly"></a>語言剖析器類別 '\<class name > ' 未正確執行

錯誤訊息：「語言剖析器類別\<的類別名稱 > ' 未正確執行。 請洽詢廠商以取得更新的剖析器模組。」

使用中的語言已註冊的設計工具類別不是衍生自正確的基類。 請洽詢您所使用之語言的廠商。

### <a name="the-name-name-is-already-used-by-another-object"></a>名稱 '\<name > ' 已經由另一個物件使用

這是 Visual Studio 序列化程式中的內部錯誤。 如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。

### <a name="the-object-object-name-does-not-implement-the-icomponent-interface"></a>物件\<的物件名稱 > ' 未執行 IComponent 介面

Visual Studio 嘗試建立元件，但建立的物件未執行<xref:System.ComponentModel.IComponent>介面。 請洽詢元件廠商以取得修正。

### <a name="the-object-object-name-returned-null-for-the-property-property-name-but-this-is-not-allowed"></a>物件\<的物件名稱 > ' 為\<屬性的屬性名稱 > ' 傳回 null，但不允許這種情況

有些 .NET 屬性應該一律會傳回物件。 例如，表單的**controls**集合應該一律傳回物件，即使其中沒有控制項。

若要更正這個錯誤，請確定錯誤中指定的屬性不是 null。

### <a name="the-serialization-data-object-is-not-of-the-proper-type"></a>序列化資料物件不是適當的類型

序列化程式所提供的資料物件不是符合目前正在使用之序列化程式的型別實例。 請洽詢元件廠商。

### <a name="the-service-service-name-is-required-but-could-not-be-located"></a>服務 '\<服務名稱 > ' 是必要的，但找不到

錯誤訊息：「服務\<」服務名稱 > ' 是必要的，但找不到。 您的 Visual Studio 安裝可能有問題。」

Visual Studio 所需的服務無法使用。 如果您嘗試載入不支援該設計工具的專案，請使用 [程式碼編輯器] 來進行所需的變更。 否則，如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。

### <a name="the-service-instance-must-derive-from-or-implement-interface-name"></a>服務實例必須衍生自或執行 '\<介面名稱 > '

此錯誤表示元件或元件設計工具已呼叫**AddService**方法，這需要介面和物件，但指定的物件未執行指定的介面。 請洽詢元件廠商。

### <a name="the-text-in-the-code-window-could-not-be-modified"></a>無法修改程式碼視窗中的文字

錯誤訊息：「無法修改程式碼視窗中的文字。 檢查檔案不是唯讀的，而且有足夠的磁碟空間。」

當 Visual Studio 因為磁碟空間或記憶體問題而無法編輯檔案，或檔案標示為唯讀時，就會發生此錯誤。

### <a name="the-toolbox-enumerator-object-only-supports-retrieving-one-item-at-a-time"></a>工具箱列舉值物件一次只支援擷取一個項目

如果您看到此錯誤，如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。

### <a name="the-toolbox-item-for-component-name-could-not-be-retrieved-from-the-toolbox"></a>無法從工具箱抓取 '\<component name > ' 的工具箱專案

錯誤訊息：「無法從工具箱抓取 '\<component name > ' 的工具箱專案。 請確定已正確安裝包含 [工具箱] 專案的元件。 工具箱專案引發下列錯誤： \<錯誤字串 >。」

有問題的元件在 Visual Studio 存取時擲回例外狀況。 請洽詢元件廠商。

### <a name="the-toolbox-item-for-toolbox-item-name-could-not-be-retrieved-from-the-toolbox"></a>無法從工具箱抓取 '\<工具箱專案名稱 > ' 的工具箱專案

錯誤訊息：「無法從工具箱抓取 '\<工具箱專案名稱 > ' 的工具箱專案。 請嘗試從 [工具箱] 中移除該專案，然後再將它加回。」

如果 [工具箱] 專案內的資料損毀或元件版本已變更，就會發生這個錯誤。 請嘗試從 [工具箱] 移除該專案，然後再次將它重新加入。

### <a name="the-type-type-name-could-not-be-found"></a>找不到\<類型 ' type name > '

錯誤訊息：找不到「\<類型 ' 類型名稱 >」。 請確定已參考包含該類型的元件。 如果元件是目前開發專案的一部分，請確定已建立專案。」

載入設計工具時，Visual Studio 無法找到類型。 請確定已參考包含該類型的元件。 如果元件是目前開發專案的一部分，請確定已建立專案。

### <a name="the-type-resolution-service-may-only-be-called-from-the-main-application-thread"></a>只能從主應用程式的執行緒中呼叫類型解析服務

Visual Studio 嘗試從錯誤的執行緒存取所需的資源。 當用來建立設計工具的程式碼從主應用程式執行緒以外的執行緒呼叫型別解析服務時，就會顯示此錯誤。 若要更正此錯誤，請從正確的執行緒呼叫服務，或洽詢元件廠商。

### <a name="the-variable-variable-name-is-either-undeclared-or-was-never-assigned"></a>變數 '\<variable name > ' 未宣告或從未指派

原始程式碼具有未宣告或指派之變數的參考（例如**Button1**）。 如果尚未指派變數，此訊息就會顯示為警告，而不是錯誤。

### <a name="there-is-already-a-command-handler-for-the-menu-command-menu-command-name"></a>功能表命令\<的功能表命令名稱 > ' 已經有命令處理常式

如果協力廠商設計工具將已經有處理常式的命令加入命令資料表中，就會發生這個錯誤。 請洽詢元件廠商。

### <a name="there-is-already-a-component-named-component-name"></a>已經有名為 '\<component name > ' 的元件

錯誤訊息：「已經有名為 '\<component name > ' 的元件。 元件必須有唯一的名稱，而且名稱不得區分大小寫。 名稱也不能與繼承類別中任何元件的名稱衝突。」

當屬性視窗中的元件名稱有所變更時，就會出現這個錯誤訊息。 若要更正這個錯誤，請確定所有元件名稱都是唯一的、不區分大小寫，而且不會與繼承類別中任何元件的名稱衝突。

### <a name="there-is-already-a-toolbox-item-creator-registered-for-the-format-format-name"></a>已經為 [格式名稱 >] 格式\<註冊工具箱專案建立者

協力廠商元件對 [工具箱] 索引標籤上的專案進行回呼，但該專案已包含回呼。 請洽詢元件廠商。

### <a name="this-language-engine-does-not-support-a-codemodel-with-which-to-load-a-designer"></a>此語言引擎不支援使用 CodeModel 載入設計工具

此訊息類似「此檔案的語言不支援必要的程式碼剖析和產生服務」，但此訊息牽涉到內部註冊問題。 如果您看到此錯誤，如果您看到此錯誤，請使用 [回報[問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)] 來記錄問題。

### <a name="type-type-name-does-not-have-a-constructor-with-parameters-of-types-parameter-type-names"></a>類型 '\<type name\>' 沒有具有參數類型為 '\<參數類型名稱 > ' 的函式

Visual Studio 找不到具有相符參數的[函數](/dotnet/csharp/programming-guide/classes-and-structs/constructors)。 這可能是因為所需的型別不是必要的類型而提供的。 例如，**點**函數可能會採用兩個整數。 如果您提供浮動，就會引發此錯誤。

若要更正這個錯誤，請使用不同的函式，或明確地轉換參數類型，使其符合由函式所提供的型別。

### <a name="unable-to-add-reference-reference-name-to-the-current-application"></a>無法將參考 '\<參考名稱 > ' 加入至目前的應用程式

錯誤訊息：「無法將參考 '\<參考名稱 > ' 加入至目前的應用程式。 檢查是否有不同版本的 '\<reference name > ' 尚未參考。」

Visual Studio 無法加入參考。 若要更正此錯誤，請檢查是否有其他版本的參考尚未被參考。

### <a name="unable-to-check-out-the-current-file"></a>無法簽出目前的檔案

錯誤訊息：「無法簽出目前的檔案。 檔案可能已鎖定，或您可能需要手動簽出檔案。」

當您將目前簽入的檔案變更為原始程式碼控制時，就會發生這個錯誤。 Visual Studio 通常會顯示 [檔案簽出] 對話方塊，讓使用者可以簽出檔案。 這次檔案未簽出，可能是因為在簽出期間發生合併衝突。 若要更正此錯誤，請確定檔案未鎖定，然後嘗試手動簽出檔案。

### <a name="unable-to-find-page-named-options-dialog-box-tab-name"></a>找不到名為\<[選項對話方塊索引標籤名稱 >] 的頁面

當元件設計工具使用不存在的名稱，從 [選項] 對話方塊要求存取頁面時，就會發生這個錯誤。 請洽詢元件廠商。

### <a name="unable-to-find-property-property-name-on-page-options-dialog-box-tab-name"></a>在頁面上的\< \<[選項] 對話方塊索引標籤名稱 > ' 中找不到屬性 ' 屬性名稱 > '

當元件設計工具要求 [選項] 對話方塊中的頁面上有特定值的存取權，但該值不存在時，就會發生這個錯誤。 請洽詢元件廠商。

### <a name="visual-studio-cannot-open-a-designer-for-the-file-because-the-class-within-it-does-not-inherit-from-a-class-that-can-be-visually-designed"></a>Visual Studio 無法開啟這個檔案的設計工具，因為它裡面的類別不會從能以視覺化方式設計的類別繼承

Visual Studio 已載入類別，但無法載入該類別的設計工具。 Visual Studio 需要設計工具使用檔案中的第一個類別。 若要更正這個錯誤，請移動類別程式碼，使其成為檔案中的第一個類別，然後再次載入設計工具。

### <a name="visual-studio-cannot-save-or-load-instances-of-the-type-type-name"></a>Visual Studio 無法儲存或載入類型 '\<type name > ' 的實例

這是協力廠商元件的問題。 請洽詢元件廠商。

### <a name="visual-studio-is-unable-to-open-document-name-in-design-view"></a>Visual Studio 無法在設計檢視中開啟\<「檔案名稱 >」

錯誤訊息：「Visual Studio 無法在設計檢視中開啟\<「檔案名稱 >」。 未安裝檔案類型的剖析器。」

此錯誤表示專案的語言不支援設計工具，而且當您嘗試在 [開啟檔案] 對話方塊或方案總管中開啟檔案時，就會發生此問題。 相反地，請在程式碼視圖中編輯檔案。

### <a name="visual-studio-was-unable-to-find-a-designer-for-classes-of-type-type-name"></a>Visual Studio 找不到類型\<為「類型名稱 >」之類別的設計工具

Visual Studio 已載入類別，但無法設計類別。 相反地，請在程式碼視圖中編輯類別，方法是以滑鼠右鍵按一下類別，然後選擇 [ **View Code**]。

## <a name="see-also"></a>另請參閱

- [使用設計工具開發 Windows Forms 控制項](developing-windows-forms-controls-at-design-time.md)
- [Windows Form 設計工具論壇](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)
