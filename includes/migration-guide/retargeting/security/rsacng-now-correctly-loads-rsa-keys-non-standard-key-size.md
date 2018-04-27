### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng 現在會正確地載入非標準金鑰大小的 RSA 金鑰

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.6.2 之前，使用非標準的 RSA 憑證金鑰大小客戶，無法透過 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> 和 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> 擴充方法存取這些金鑰。  會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> 以及「不支援要求的金鑰大小」訊息。 在 .NET Framework 4.6.2 中，已修正此問題。 同樣地，<xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> 和 <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> 現在可以使用非標準的金鑰大小，而不會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>。|
|建議|如果有任何例外狀況處理邏輯會依賴先前的行為，也就是使用非標準的金鑰大小時會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>，請考慮移除該邏輯。|
|範圍|Edge|
|版本|4.6.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|

