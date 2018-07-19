# [SQL Server 2014 アップグレード アドバイザー](sql-server-2014-upgrade-advisor.md)
# [アップグレード アドバイザーのインストール](installing-upgrade-advisor.md)
## [アップグレード アドバイザーの前提条件](upgrade-advisor-prerequisites.md)
## [コマンド プロンプトからのアップグレード アドバイザーのインストール](installing-upgrade-advisor-from-the-command-prompt.md)

# [アップグレード アドバイザーの使用](working-with-upgrade-advisor.md)
# [アップグレード アドバイザーの概要](overview-of-upgrade-advisor.md)
## [アップグレード プロセスの概要](upgrade-process-overview.md)
## [アップグレード アドバイザーの概要](upgrade-advisor-overview.md)
## [アップグレード アドバイザーの実行 (ユーザー インターフェイス)](running-upgrade-advisor-user-interface.md)
## [アップグレード アドバイザーの実行 (コマンド プロンプト)](running-upgrade-advisor-command-prompt.md)
## [レポートの使用](using-reports.md)
## [アップグレード アドバイザー エラー](upgrade-advisor-errors.md)
# [アップグレード アドバイザーの操作方法に関するトピック](upgrade-advisor-how-to-topics.md)
## [アップグレード アドバイザーをインストールする方法](how-to-install-upgrade-advisor.md)
## [アップグレード アドバイザーを起動する方法](how-to-launch-upgrade-advisor.md)
## [アップグレード アドバイザー分析ウィザードを実行する方法](how-to-run-the-upgrade-advisor-analysis-wizard.md)
## [アップグレード アドバイザーのレポートを表示する方法](how-to-view-an-upgrade-advisor-report.md)
## [レポートに表示する問題を選択する方法](how-to-filter-reports.md)
## [レポートをエクスポートする方法](how-to-export-reports.md)
# [ユーザー インターフェイス リファレンス](upgrade-advisor-user-interface-reference.md)
## [SQL Server のコンポーネント](sql-server-components.md)
## [接続パラメーター](connection-parameters.md)
## [SQL Server パラメーター](sql-server-parameters.md)
## [Analysis Services パラメーター](analysis-services-parameters.md)
## [Reporting Services パラメーター](reporting-services-parameters.md)
## [Integration Services パラメーター](integration-services-parameters.md)
## [アップグレード アドバイザーの設定を確認](confirm-upgrade-advisor-settings.md)
## [アップグレード アドバイザーの進行状況](upgrade-advisor-progress.md)

# [アップグレードに関する問題の解決](resolving-upgrade-issues.md)
## [アップグレードに関する最新の問題](late-breaking-upgrade-issues.md)
## [データベース エンジンのアップグレードに関する問題](database-engine-upgrade-issues.md)
### [0xFFFF 文字はオブジェクト識別子としては無効である](0xffff-character-is-not-valid-as-an-object-identifier.md)
### [アップグレード後に、予約された新しいキーワードを識別子として使用できない](after-upgrade-new-reserved-keywords-cannot-be-used-as-identifiers.md)
### [string-length および substring の動作の変更](changes-to-behavior-of-string-length-and-substring.md)
### [syslockinfo および sp_lock の動作に対する変更](changes-to-behavior-in-syslockinfo-and-sp-lock.md)
### [トレース フラグの動作が変更された](changes-to-behavior-of-trace-flags.md)
### [SQL Server Reporting Services Standard および Enterprise での CPU およびメモリの制限の変更点](cpu-memory-limits-changes-sql-server-reporting-services-standard-enterprise.md)
### [xs:dateTime 型、xs:date 型、および xs:time 型のストレージ形式の変更](changes-to-the-storage-format-for-types-xs-datetime-xs-date-and-xs-time.md)
### [ORDER BY 句の列の別名をテーブル別名によってプレフィックス指定できない](column-aliases-in-order-by-clause-cannot-be-prefixed-by-table-alias.md)
### [非推奨の DBCC コマンドが削除された](deprecated-dbcc-commands-have-now-been-removed.md)
### [データベース ID 32767 をデタッチする](detach-database-id-32767.md)
### [休止している SQL Server 6.5 ログインはアップグレードできない](dormant-sql-server-6-5-logins-cannot-be-upgraded.md)
### [互換性モードが 90 以上の場合、FOR BROWSE はビューで使用できません](for-browse-is-not-allowed-in-views-in-90-or-later-compatibility-modes.md)
### [互換性モード 90 以上では FOR XML AUTO クエリが派生テーブルの参照を返す](for-xml-auto-queries-return-derived-table-references-90-later-compatibility-mode.md)
### [INFORMATION_SCHEMA.SCHEMATA がインスタンスのデータベースではなく、データベースのスキーマ名を返す](information-schema-schemata-returns-schema-names-not-databases.md)
### [無効な名前付きパイプ名によってアップグレードがブロックされる](invalid-named-pipe-name-can-block-upgrade.md)
### [バックアップまたは復元のサイズの大きい履歴テーブルではアップグレードが応答を停止したように見える](large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond.md)
### [90 以上の互換性モードでは大きな定数が大きな値の型として指定される](large-constants-typed-as-large-value-types-90-later-compatibility-mode.md)
### [アップグレード後にログ配布が実行されない](log-shipping-will-not-run-after-upgrading.md)
### [sysperfinfo.cntr_value から bigint 型の値を受け取れるようにアプリケーションを変更する](modify-applications-to-expect-bigint-values-from-sysperfinfo-cntr-value.md)
### [Banyan VINES Sequenced Packet Protocol (SPP)、Multiprotocol、AppleTalk、または NWLink IPX/SPX ネットワーク プロトコルを使用する接続を変更する](modify-connections-banyan-vines-spp-multiprotocol-appletalk-nwlink-ipx-spx.md)
### [HOST_ID の戻り型に依存するインデックスを変更する](modify-indexes-that-depend-on-the-return-type-of-host-id.md)
### [バイナリ ラージ オブジェクト (BLOB) を読み書きする UPDATETEXT ステートメントを変更する](modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs.md)
### [トリガーの入れ子がオフになっている場合でも、入れ子になった AFTER トリガーが起動される](nested-after-trigger-fires-even-when-trigger-nesting-is-off.md)
### [sp_helptrigger 出力の新しい列がアプリケーションに影響を与える可能性がある](new-column-in-output-of-sp-helptrigger-may-impact-applications.md)
### [osql は ED コマンドと !! コマンドをサポートしない](osql-no-longer-supports-the-ed-and-commands.md)
### [互換性モード 90 以上では外部結合演算子 *= および =* がサポートされない](outer-join-operators-and-are-not-supported-in-90-or-later-compatibility-modes.md)
### [読み取り専用データベースをアップグレードできない](read-only-databases-cannot-be-upgraded.md)
### [非推奨の DBCC CONCURRENCYVIOLATION コマンド呼び出しの削除](remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command.md)
### [予約されたキーワードの後のコロンを削除する](remove-colon-following-reserved-keyword.md)
### [DML トリガー内の inserted テーブルと deleted テーブルに対する DDL 操作を削除する](remove-ddl-operations-on-the-inserted-and-deleted-tables-inside-dml-triggers.md)
### [推奨されないシステム ストアド プロシージャの参照の削除](remove-references-to-deprecated-system-stored-procedures.md)
### [ドキュメントに記載されていないシステム テーブルへの参照の削除](remove-references-to-undocumented-system-tables.md)
### [システム オブジェクトを破棄するステートメントを削除する](remove-statements-that-drop-system-objects.md)
### [システム オブジェクトの列レベル権限を変更するステートメントを削除する](remove-statements-that-modify-column-level-permissions-on-system-objects.md)
### [システム オブジェクトを変更するステートメントを削除する](remove-statements-that-modify-system-objects.md)
### [変更データ キャプチャを有効にする場合に cdc スキーマを削除する](remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture.md)
### [固定サーバー ロール名と一致するログイン名を変更する](rename-logins-matching-fixed-server-role-names.md)
### [予約されている DATE データ型および TIME データ型に基づいて名前が付けられた UDT の削除](remove-udt-s-named-after-the-reserved-date-and-time-data-types.md)
### [予約されている ORDPATH データ型に基づいて名前が付けられた UDT の削除](remove-udt-s-named-after-the-reserved-ordpath-data-type.md)
### [予約されている GEOMETRY データ型および GEOGRAPHY データ型に基づいて名前が付けられた UDT の削除](remove-udts-named-after-the-reserved-geometry-and-geography-data-types.md)
### [ユーザー sys の名前変更が必要](rename-user-sys.md)
### [SQL Server 2005 では SERVERPROPERTY が LCID プロパティの正しい結果を返す](serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005.md)
### [ドメイン コントローラーで SQL Server 2008 へのアップグレードを実行するためのサービス アカウント要件](service-account-requirements-upgrade-sql-server-2008-on-domain-controller.md)
### [互換性モード 90 ではテーブル ヒントを使用するときに WITH キーワードを指定する](specify-the-with-keyword-when-using-table-hints-in-90-compatibility-mode.md)
### [SQL Server のネイティブ SOAP サポートは、このバージョンの SQL Server では継続されません。](sql-server-native-soap-support-is-discontinued-in-this-version-of-sql-server.md)
### [インデックス付きビュー定義のテーブル ヒントが互換性モード 80 では無視され、互換性モード 90 以上では許可されない](table-hints-indexed-views-ignored-80-compatibility-mode-not-allowed-90-later.md)
### [OPENXML XPath 式の更新によりサポートされていない関数が削除される](update-openxml-xpath-expressions-to-remove-unsupported-functions.md)
### [sp_rename を使用して重複するインデックス名を変更する](use-sp-rename-to-rename-duplicate-index-name.md)
### [完全なパスを使用して、拡張ストアド プロシージャ DLL の名前を登録する](use-the-full-path-to-register-extended-stored-procedure-dll-names.md)
### [system_function_schema でユーザー定義関数が許可されない](user-defined-functions-are-not-allowed-in-system-function-schema.md)
### [アップグレード処理中にすべてのファイル グループが書き込み可能であることを確認する](verify-all-filegroups-are-writeable-during-the-upgrade-process.md)
### [アップグレード処理中、すべてのデータ ファイルとログ ファイルの自動拡張が有効になっていることを確認する](verify-autogrow-turned-on-for-all-data-and-log-files-during-upgrade.md)
### [アップグレード処理中にデータベース ファイルが圧縮ドライブにないことを確認する](verify-no-database-files-on-compressed-drives-during-upgrade.md)
### [幾何学、地理学、HIERARCHYID のクライアント側の使用に関する警告](warning-about-client-side-usage-of-geometry-geography-and-hierarchyid.md)
### [Web Assistant ストアド プロシージャが削除された](web-assistant-stored-procedures-have-been-removed.md)
### [WinSock プロキシ構成はサポートされていない](winsock-proxy-configuration-not-supported.md)
### [互換性モード 90 以上では TOP を含むビューで WITH CHECK OPTION がサポートされない](with-check-option-not-supported-in-top-views-90-later-compatibility-mode.md)
### [互換性モード 90 以上では CREATE STATISTICS ステートメントで WITH ROWS がサポートされない](with-rows-not-supported-in-create-statistics-statements-90-later-compatibility-mode.md)
### [データベース エンジンのアップグレードに関するその他の問題](other-database-engine-upgrade-issues.md)
#### [データベース ミラーリングの Deprecation Announcement](database-mirroring-deprecation-announcement.md)
## [フルテキスト検索のアップグレードに関する問題](full-text-search-upgrade-issues.md)
### [フルテキスト検索は SQL Server 2008 以降変更されています](full-text-search-has-changed-since-sql-server-2008.md)
### [SQL Server 2005 および SQL Server 2008 では、フルテキスト検索ワード ブレーカーとフィルターが大幅に機能向上](full-text-search-word-breakers-filters-improved-sql-server-2005-2008.md)
### [フルテキスト カタログ名が最長 120 文字に制限されている](length-of-full-text-catalog-names-restricted-to-120-characters.md)
### [既定では Microsoft Full-Text Engine for SQL Server は署名のないサード パーティ コンポーネントを読み込まない](full-text-engine-sql-server-default-will-not-load-third-party-components.md)
### [廃止されたフルテキスト検索プロパティを使用するストアド プロシージャを変更する](modify-stored-procedures-that-use-discontinued-full-text-search-properties.md)
### [保存されない計算列にフルテキスト インデックスを使用できない](full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed.md)
### [master、tempdb、および model データベースに対するフルテキスト インデックスはサポートされない](full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported.md)
### [既定では、アップグレードにより、グローバルではなく、インスタンス レベルのワード ブレーカーおよびフィルターがフルテキスト検索で使用される](full-text-search-uses-instance-not-global-level-defaults-after-upgrade.md)
### [アップグレード後、フルテキスト検索では、OUTPUT INTO 式で述語を使用できない](full-text-search-will-not-allow-predicates-in-output-into-expressions-after-upgrade.md)
## [レプリケーションのアップグレードに関する問題](replication-upgrade-issues.md)
### [アップグレードすると、メッセージ キューを使用するキュー更新サブスクリプションが変更される](upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing.md)
### [レプリケーションのアップグレードに関するその他の問題](other-replication-upgrade-issues.md)
## [Reporting Services のアップグレードに関するその他の問題 (アップグレード アドバイザー)](reporting-services-upgrade-issues-upgrade-advisor.md)
### [レポート サーバー Web サイト上のクライアント証明書 (アップグレード アドバイザー)](client-certificates-on-the-report-server-web-site-upgrade-advisor.md)
### [レポート サーバーでカスタム拡張機能が検出された (アップグレード アドバイザー)](custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)
### [カスタム レポート アイテムがレポート サーバーで検出された (アップグレード アドバイザー)](custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)
### [IIS の下位互換コンポーネントが検出されない (アップグレード アドバイザー)](iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)
### [IP アドレス制限が検出された (アップグレード アドバイザー)](ip-address-restriction-detected-upgrade-advisor.md)
### [ISAPI フィルターがレポート サーバー サイトで検出された (アップグレード アドバイザー)](isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)
### [互換性のために残されている拡張機能がレポート サーバー コンピューターで検出された (アップグレード アドバイザー)](obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)
### [レポート サーバー データベースが構成されていない (アップグレード アドバイザー)](report-server-database-is-not-configured-upgrade-advisor.md)
### [SQL Server 2005 レポート サーバー Web サービス グループが検出された (アップグレード アドバイザー)](sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)
### [仮想ディレクトリが指定されていない (アップグレード アドバイザー)](virtual-directories-are-unspecified-upgrade-advisor.md)
### [仮想ディレクトリにサポートされていない認証方法がある (アップグレード アドバイザー)](virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)
### [SQL Server Standard および Enterprise での CPU およびメモリの制限の変更点 (アップグレード アドバイザー)](cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)
### [SharePoint ファームに必要なドメイン アカウント (アップグレード アドバイザー)](domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)
### [レポート サーバーの直接参照 (アップグレード アドバイザー)](direct-browsing-to-report-server-upgrade-advisor.md)
### [Microsoft SharePoint 2007 がインストールされている (アップグレード アドバイザー)](microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)
### [Microsoft SQL Server Reporting Services SharePoint 共有サービスがサイド バイ サイドでインストールされている (アップグレード アドバイザー)](sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)
### [互換性のないデータベース エンジン サーバーの照合順序 (アップグレード アドバイザー)](incompatible-database-engine-server-collation-upgrade-advisor.md)
### [Reporting Services のアップグレードに関するその他の問題](other-reporting-services-upgrade-issues.md)
## [SQL Server エージェントのアップグレードに関する問題](sql-server-agent-upgrade-issues.md)
### [データベース メンテナンス プランが新しくなった](database-maintenance-plans-superseded.md)
### [sysadmin ユーザーのみがジョブ ステップのログ ファイルをファイル システムに書き込むことができる](only-sysadmin-users-can-write-job-step-log-files-to-the-file-system.md)
### [xp_sqlagent_proxy_account 拡張ストアド プロシージャの代わりに新しいストアド プロシージャを使用する](replace-xp-sqlagent-proxy-account-extended-sp-with-new-stored-procedures.md)
### [SQL Server エージェントのログ配布ジョブ カテゴリが原因でアップグレードに失敗する](sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)
### [SQL Server エージェント サービスで SQL Server 認証を使用できない](sql-server-agent-service-cannot-use-sql-server-authentication.md)
### [SQL Server エージェントのジョブ ステップのトークン構文を更新する](update-token-syntax-in-sql-server-agent-job-steps.md)
### [マスター サーバーをアップグレードする前にすべての対象サーバーをアップグレードする](upgrade-all-target-servers-before-upgrading-the-master-server.md)
### [アップグレードすると SQL Server エージェント ユーザーのプロキシ アカウントが一時的な UpgradedProxyAccount に変更される](upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)

# [セットアップとサービスのインストール](setup-and-servicing-installation.md)
## [SQL Server のライセンスに関する注意点](licensing-considerations-for-sql-server.md)
# [SQL Server セットアップのドキュメントの概要](overview-of-sql-server-setup-documentation.md)
# [SQL Server 2014 セットアップのユーザー インターフェイス](sql-server-2014-setup-user-interface.md)

# [SQL Server セットアップのユーザー インターフェイス リファレンス](sql-server-setup-user-interface-reference.md)
## [使用許諾条件への同意](accept-license-terms.md)
## [SQL Server フェールオーバー クラスター ノードの追加](add-sql-server-failover-cluster-node.md)
## [Analysis Services の構成 - アカウントの準備](analysis-services-configuration-account-provisioning.md)
## [Analysis Services の構成 - データ ディレクトリ](analysis-services-configuration-data-directories.md)
## [クラスター ディスクの選択](cluster-disk-selection.md)
## [クラスター ネットワークの構成](cluster-network-configuration.md)
## [クラスター ノードの構成](cluster-node-configuration.md)
## [クラスター ノードの構成 (完了)](cluster-node-configuration-complete.md)
## [クラスター リソース グループ](cluster-resource-group.md)
## [クラスターのセキュリティ ポリシー](cluster-security-policy.md)
## [完了 - イメージの完了](complete-complete-image.md)
## [イメージの完了の進行状況](complete-image-progress.md)
## [イメージの完了ルール](complete-image-rules.md)
## [完了 - イメージの準備](complete-prepare-image.md)
## [完了 - 修復](complete-repair.md)
## [完了 - アップグレード](complete-upgrade.md)
## [データベース エンジンの構成 - アカウントの準備](database-engine-configuration-account-provisioning.md)
## [データベース エンジンの構成 - データ ディレクトリ](database-engine-configuration-data-directories.md)
## [データベース エンジンの構成 - Filestream](database-engine-configuration-filestream.md)
## [データベース エンジンの構成 - ユーザー インスタンス](database-engine-configuration-user-instance.md)
## [分散再生コントローラーの構成](distributed-replay-controller-configuration.md)
## [分散再生クライアントの構成](distributed-replay-client-configuration.md)
## [エディションのアップグレード規則](edition-upgrade-rules.md)
## [フェールオーバー クラスター レポート](failover-cluster-report.md)
## [機能の確認](feature-review.md)
## [インストール ルール](installation-rules.md)
## [機能ルール](feature-rules.md)
## [機能の選択](feature-selection.md)
## [機能の選択 (アンインストール)](feature-selection-uninstall.md)
## [機能の選択 (アップグレード)](select-features-upgrade.md)
## [フルテキスト検索アップグレード オプション](full-text-search-upgrade-options.md)
## [完了 - インストール](complete-installation.md)
## [インストールの前提条件](installation-prerequisites.md)
## [インストールの進行状況](installation-progress.md)
## [インストールの種類](installation-type.md)
## [インスタンスの構成](instance-configuration.md)
## [インスタンスの選択 (アンインストール)](instance-selection-uninstall.md)
## [インスタンスの選択 (アップグレード)](instance-selection-upgrade.md)
## [インスタンスの選択](select-instance.md)
## [アンインストール後](post-uninstall.md)
## [イメージの準備の進行状況](prepare-image-progress.md)
## [イメージの準備ルール](prepare-image-rules.md)
## [イメージの種類の準備](prepare-image-type.md)
## [プロダクト キー](product-key.md)
## [進行状況 (アンインストール)](progress-uninstall.md)
## [イメージの完了の準備完了](ready-to-complete-image.md)
## [インストールの準備完了](ready-to-install.md)
## [イメージの準備の準備完了](ready-to-prepare-image.md)
## [修復の準備完了](ready-to-repair.md)
## [SQL Server フェールオーバー クラスター ノードの削除](remove-sql-server-failover-cluster-node.md)
## [修復の進行状況](repair-progress.md)
## [Reporting Services 構成オプション](reporting-services-configuration-options-ssrs.md)
## [Reporting Services SharePoint モードのアップグレード](reporting-services-sharepoint-mode-upgrade-ssrs.md)
## [Reporting Services SharePoint モード認証](reporting-services-sharepoint-mode-authentication.md)
## [準備済みインスタンスの選択](select-a-prepared-instance.md)
## [サーバーの構成 - 照合順序](server-configuration-collation.md)
## [サーバーの構成 - サービス アカウント](server-configuration-service-accounts.md)
## [セットアップ ロール](setup-role.md)
## [SQL Server フェールオーバー クラスター ウィザード - 完了](sql-server-failover-cluster-wizard-complete.md)
## [SQL Server フェールオーバー クラスター ウィザード - インストール](sql-server-failover-cluster-wizard-install.md)
## [SQL Server フェールオーバー クラスター ウィザード - 準備](sql-server-failover-cluster-wizard-prepare.md)
## [アップグレードの準備完了](ready-to-upgrade.md)
## [インストール ルール](install-rules.md)
## [アンインストール ルール](uninstallation-rules.md)
## [アップグレードの進行状況](upgrade-progress.md)
## [機能ルール (アップグレード)](feature-rules-upgrade.md)
## [アンインストール オプションの確認](verify-uninstall-options.md)

# [SQL Server サービスのインストール](sql-server-servicing-installation.md)
## [コマンド プロンプトからの更新プログラムのインストール](../../database-engine/install-windows/installing-updates-from-the-command-prompt.md)
## [SQL Server 更新プログラムのインストールが成功したかどうかを確認する方法](how-to-validate-successful-installation-of-a-sql-server-update.md)
## [SQL Server サービスのインストールの概要](overview-of-sql-server-servicing-installation.md)
## [ようこそ](welcome.md)
## [ライセンス条項](license-terms.md)
## [機能の選択](select-features.md)
## [使用中のファイルの確認](check-files-in-use.md)
## [更新準備完了](ready-to-update.md)
## [更新の進行状況](update-progress.md)
## [完了](complete.md)