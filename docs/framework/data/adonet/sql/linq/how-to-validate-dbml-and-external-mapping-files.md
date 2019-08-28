---
title: 作法：驗證 DBML 和外部對應檔
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 212d65dfe998b825dd40e564756083ed685dff6f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041136"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>作法：驗證 DBML 和外部對應檔

如果修改外部對應檔案和 .dbml 檔案，則必須根據它們各自的結構描述定義進行驗證。 本主題為 Visual Studio 使用者提供執行驗證程式的步驟。

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a>若要驗證 .dbml 或 XML 檔案

1. 在 [Visual Studio檔案] 功能表上, 指向 [**開啟**],然後按一下 [檔案]。

2. 在 [**開啟**檔案] 對話方塊中, 按一下您要驗證的 .DBML 或 XML 對應檔。

    檔案會在**XML 編輯器**中開啟。

3. 在視窗上按一下滑鼠右鍵, 然後按一下 [**屬性**]。

4. 在 [**屬性**] 視窗中, 按一下 [**架構**] 屬性的省略號。

    [ **XML 架構**] 對話方塊隨即開啟。

5. 請記下適用於您目的的適當結構描述定義。

    - DbmlSchema.xsd 是用來驗證 .dbml 檔案的結構描述定義。 如需詳細資訊, 請參閱[LINQ to SQL 中的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。

    - LinqToSqlMapping.xsd 是用來驗證外部 XML 對應檔案的結構描述定義。 如需詳細資訊, 請參閱[外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。

6. 在 [**使用**所需架構定義的資料行] 資料列中, 按一下以開啟下拉式清單方塊, 然後按一下 [**使用此架構**]。

    結構描述定義檔案現在已經與 DBML 或 XML 對應檔案產生關聯。

    請確定未選取其他結構描述定義。

7. 在 [ **View** ] 功能表上, 按一下 [**錯誤清單**]。

    判斷是否已產生錯誤、警告或訊息。 如果未產生，則會根據結構描述定義驗證 XML 檔案為有效。

## <a name="alternate-method-for-supplying-schema-definition"></a>提供結構描述定義的替代方法

如果因為某些原因而適當的 .xsd 檔案未出現在 [ **XML 架構**] 對話方塊中, 您可以從說明主題下載 .xsd 檔案。 下列步驟可協助您以 Visual Studio XML 編輯器所需的 Unicode 格式儲存下載的檔案。

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>若要從說明主題中複製結構描述定義檔案

1. 如這個主題前面所述，找到內含結構描述定義的 [說明] 主題。

    - 如需 .dbml 檔案, 請參閱[LINQ to SQL 中的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。

    - 如需外部對應檔案, 請參閱[外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。

2. 按一下 [**複製程式碼**], 將程式碼檔案複製到剪貼簿。

3. 啟動 [記事本]，建立新的檔案。

4. 將剪貼簿中的程式碼貼入 [記事本] 檔案中。

5. 在 [記事本檔案] 功能表上, 按一下 [**另存**新檔]。

6. 在 [**編碼**] 方塊中, 選取 [ **Unicode**]。

    > [!IMPORTANT]
    > 這個選項可確保會在文字檔前面加上 Unicode 16 位元組順序標記 (`FFFE`)。

7. 在 [**檔案名**] 方塊中, 建立副檔名為 .xsd 的檔案名。

## <a name="see-also"></a>另請參閱

- [參考資料](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
