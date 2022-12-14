# コンピューティングサービス

1. EC2
  - EC2の概要
    - `EC2`は`Amazon Elstic Compute Cloud`の略
  - EC2の特徴
    - 必要なときに必要な量だけの量を使用
    - 使用した分だけにだけコストが発生
    - 変更可能なインスタンスタイプから性能を選択
    - 数分でサーバを調達して、起動できる
    - 世界中のリージョンから起動場所を選択
    - `AMI`からいつでも同じサーバを起動できる
    - セキュリティグループでトラフィックを制御できる
    - オペレーティングシステムを管理者権限で操作できる
    - ユースケースに応じた料金オプション
  - `ポイント`
    - 使うときにだけEC2インスタンスを起動することができる
    - 必要なEC2インスタンスの数を事前に予測する必要はない
  - `コスト-ポイント`
    - 使った分にだけ料金が発生する
    - 時間単位、秒単位で課金される
    - アウト通信に転送料金が発生する
  - `インスタンスタイプ-ポイント`
    - インスタンスタイプは運用を開始した後に柔軟に性能を変更できる
    - 運用を開始する前の誤った性能予測の計算をする必要がなくなる
  - `サーバ調達-ポイント`
    - 数分でEC2を起動できることは、経営の俊敏性を増すことに直結する
    - 数分でEC2を世界中にデプロイすることができる
  - `AMI(Amazon Machine Image)からいくつでも同じサーバを起動できる-ポイント`
    - AMIから同じ構成のEC2インスタンスを何台でも起動できる
    - AWS Marketplaceから簡単にソフトウェア構成済みのEC2インスタンスを起動できる
  - `セキュリティグループでトラフィックを制御できる-ポイント`
    - EC2インスタンスへのトラフィックはセキュリティグループのインバウンド(受信)で制御する
  - `オペレーティングシステムを管理者権限で操作できる-ポイント`
    - オペレーティングシステムの管理者はキーペアで安全にログインできる
  - `ユースケースに応じた料金オプション-ポイント`
    - `オンデマンドインスタンス`-使った分だけ料金が発生する
    - `リザーブドインスタンス`-例えば、24時間365日(または、その75%以上)稼働し続ける場合は、リザーブドインスタンスが最適である-P95参照
    - ユースケースに応じて料金オプションを使い分けることでコスト効率が向上する

2. ELB(`Elastic Load Balancing`)
  - ELB概要
    - EC2インスタンスの可用性を高めるためにELBを使用することができる
  - `ロードバランサータイプ-ポイント`
    - HTTP/HTTPSでは、Application Load Balancerを使い、それ以外はのTCPでは、Network Load Balancerを使う
  - `ヘルスチェック-ポイント`
    - ELBには、正常なインスタンスのみにトラフィックを送るためのヘルスチェック機能がある
  - `インターネット向け/内部向け`
    - ELBはインターネット向けにも内部向けにも対応している
    - インターネット向けだけではなく内部にもELBを挟むことによって、システムの可用性をさらに高めることができる
  - `高可用性のマネージドサービス`
    - ELB自体が高可用性のマネージドサービスなので単一障害点とはならない
  - `クロスゾーン負荷分散`
    - 複数のアベイラビリティゾーンに負荷分散を実行できるのでリソースの不可が均等になる

3. Auto Scaling
  - 概要
    - Auto ScalingによってEC2インスタンスを必要なときに自動で増減できる
    - Auto Scalingのメリットは、高可用性、耐障害性、コスト効率化
  - `垂直スケーリング`と`水平スケーリング`
    - P115参照
    - 垂直スケーリングよりも水平スケーリングのほうがスケーラビリティを確保しやすい
  - Auto Scalingの設定
    - Auto Scalingでは起動設定（何を）、Auto Scalingグループ（どこで）、Auto Scalingポリシー（いつ）を設定する
  - アプリケーションデプロイの自動化
    - EC2のユーザデータを使うことでコマンドを自動実行し、デプロイ処理を自動化することが可能である
    - EC2の情報(IPアドレスやインスタンスID)はメタデータからでも取得可能である
  - `ELBとAuto Scalingを使用したスケーラブルなWebアプリケーション`
    - ELB、Cloud Watch、Auto Scalingの3つのサービスで自動的なスケーラブルなアプリケーションを構築できる

4. Lambda
  - サーバ構築や環境の準備をすることなく、すぐに開発を始められる
  - サーバの運用から解放され、開発に注力できる
  - Lambdaを使うために新しい言語の学習は不要
  - リクエストに応じて、水平的にスケーリングして、並行で関数が実行される
  - Auto Scalingを設定する必要がない
  - メモリを割り当てることで他のリソースの性能も割り当てられる
  - 実行されている時間に対してミリ単位の無駄のない課金がなされる
  - 実行されていない待機時間には課金はされない
  - AWSサービスの処理を簡単に自動化できる
  - AWSサービスからのトリガーを使用することで、イベントからLambdaを実行できる

5. その他のコンピューティングサービス
  - `ECS(Amazon Elastic Container Service)` コンテナ管理を行うマネージドサービスである
  - `Lightsail` AWSが提供する仮想プライベートサーバである
  - `Batch` AWS Batchは、フルマネージド型のバッチ処理実行環境サービスである