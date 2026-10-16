# msteams-mcp: Teams sohbetleri için salt okunur MCP sunucusu (şartname deposu)

Bu depoda **kod yoktur**. Bunun yerine projenin tam şartnamesi vardır: [SPEC.md](SPEC.md).

Şartname, AI asistanının (VS Code Copilot Chat, Claude vb.) kullanıcının **kendi Teams sohbetlerini okuyabilmesi**
için kendi bilgisayarında çalışan, en az yetkiyle ve kullanıcının kendi Entra uygulaması üzerinden çalışan bir
MCP sunucusunun ne olduğunu, neden bu şekilde tasarlandığını ve nasıl yazılacağını anlatır.

*A specification for a small, self-hosted, read-only MCP server for Microsoft Teams chats (delegated permissions,
own Entra app, local stdio or loopback HTTP). This repository contains the spec, not the code: have your coding
agent write it, review it, and run it in your own tenant.*

## Neden kod yerine şartname?

Bu sunucu kuruluşunuzun Teams verisine dokunur. Hazır bir kodu olduğu gibi kurmak yerine:

* kendi Entra uygulama kaydınızla, kendi güvenlik incelemenizle yazdırın,
* her güvenlik kontrolünün testini görün (şartnamede 12 maddelik gereksinim listesi var),
* kuruma özel değerler (tenant, client id) hiçbir yerde paylaşılmasın.

## Nasıl kullanılır?

1. [SPEC.md](SPEC.md) dosyasını boş bir klasöre koyun.
2. Bölüm 2'deki ön koşulları hazırlayın (Entra'da tek tenant uygulama kaydı, `User.Read` ve `Chat.Read` temsilci izinleri).
3. Claude Code'a (ya da benzer bir kodlama ajanına) bölüm 10'daki istemi verin.
4. Ortaya çıkan kodu **kendiniz inceleyin**, bölüm 11'deki doğrulama listesini çalıştırın, gizli bilgi taraması yapın.
5. Kurulum ve işletim belgelerini de ajan yazar (bölüm 9).

## Önemli uyarılar

* **Veri, AI istemciniz üzerinden bilgisayarınızdan çıkar.** Teams mesaj metinleri MCP istemcinizin kullandığı AI
  modeline (çoğunlukla bir bulut servisi) gönderilir. Kurum verisiyle kullanmadan önce hukuk, KVKK ve BT güvenlik
  onayı alın.
* Sunucu yalnızca **kişisel iş istasyonunda, tek kullanıcı için** tasarlanmıştır. Paylaşımlı sunucuda çalıştırmayın.
* Teams verisiyle çalışırken aynı oturumda e-posta, web, dosya yazma ve GitHub gibi dışarı yazabilen MCP
  sunucularını kapalı tutun (prompt injection ile veri sızdırma riski).
* Bu şartname bir güvenlik garantisi değildir. Ortaya çıkan kod sizin sorumluluğunuzdadır.

## Lisans

MIT © 2026 Anıl Yavuz. Microsoft ile bağlantılı değildir ve Microsoft tarafından onaylanmamıştır. Microsoft,
Microsoft Teams, Microsoft Entra ve Microsoft Graph, Microsoft şirketler grubunun ticari markalarıdır.
