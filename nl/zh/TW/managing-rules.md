---

copyright:
  years: 2017
lastupdated: "2017-11-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 管理防火牆規則（原則）

FortiGate 利用「原則」的概念，其中包括接受/拒絕資料流量、套用安全設定檔、調整資料流量、記載資料流量，以及為要套用的原則排定時間表等功能。
若要彙編原則，您必須先建立將參與其中的物件。 

1. 使用[客戶入口網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://control.softlayer.com/){: new_window} 的**裝置詳細資料**頁面中找到的認證來登入應用裝置。請遵循如何[管理 FortiGate 安全應用裝置](managing-fsa.html)指示來尋找認證。
2. 登入應用裝置之後，導覽至**原則及物件**功能表，然後選取您想要管理的通訊協定（例如 IPv4 或 IPv6）。原則會根據最左邊的「序號」針對資料流量進行實作。使用者可以在清單中將原則拖高一點，以便早點進行實作，反之亦然。
3. 若要新增原則，請按一下**建立新的項目**，並參照下列這些欄位定義：

    **送入的介面：**公用型的介面（外部介面）用於進入規則，或運算型的介面（內部介面）用於外出規則。

    **來源位址：**這是資料流量的來源 IP。必須將 IP 新增至「物件功能表」上的「位址」清單中。請注意，提供「全部」選項。

    **來源使用者：**這會將原則套用至在「使用者與裝置」畫面中所建立的使用者或群組。

    **來源裝置類型：**這會將原則套用至在「使用者與裝置」畫面中所建立的裝置。

    **目的地位址：**這是資料流量的目標 IP。必須將 IP 新增至「物件功能表」上的「位址」清單中。請注意，提供「全部」選項。

    **排程：**這可決定原則何時將執行。提供「一律」選項。您也可以在「排程」下的「物件」功能表中建立排程。

    **服務：**這可決定原則將套用至其中的服務。提供「全部」選項以及許多標準服務。您可以在「物件」下的「服務」功能表中新增其他服務。

    **動作：**接受或拒絕資料流量。 

    **防火牆/網路選項：**啟用或停用 NAT 及其相關聯的選項。

    **安全設定檔：**為每個選項提供「開/關」切換，以及允許對設定檔的關聯。

    **資料流量調整：**這可讓您配置資料流量可用的最大和保證（最小）頻寬。連線數上限也可以在按照每一個 IP 的調整器上進行設定。 

    DSCP 設定無效，因為 IBM Cloud 平台會忽略使用者產生的 QoS 資訊。

    **記載選項：**配置何時記錄「允許的」資料流量。此設定（以及特別是「擷取封包」選項）會使用裝置資源。

    **註解：**使用者產生的註解

    **啟用此原則：**啟用或停用原則

## Web 資料流量進到 Web 伺服器的一個簡式「容許全部」規則的範例

***送入介面：*** *外部 VLAN*

***來源位址：*** *全部*

***來源使用者：** *空白*

***來源裝置類型：*** *空白*

***送出介面：*** *內部 VLAN*

***目的地位址：*** *x.x.x.x（Web 伺服器 IP）*

***排程：*** *一律*

***服務：*** *HTTP*

***動作：*** *接受*

***NAT：*** *關閉*

***安全設定檔：*** *使用標準*

***資料流量調整：*** *關閉*

***記載容許的資料流量：*** *開啟（安全事件）*

***註解：*** *Web 伺服器資料流量 x.x.x.x*

***啟用此原則：*** *開啟*