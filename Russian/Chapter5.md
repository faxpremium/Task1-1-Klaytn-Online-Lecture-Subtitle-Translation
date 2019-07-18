# 5. Фронт-энд для разработки игр Klaytn Addition
 
## 5.1 Настройки


Теперь, когда вы создали контракт, который будет использоваться для BApp в предыдущих классах, давайте сделаем предварительную разработку.
Сначала давайте приступим к базовой настройке.
В этом уроке я скачаю node.js, npm, инфраструктуру Truffle и код Visual Studio.
Node.js - это серверная JavaScript-платформа, которая нам реально нужна для нашего BApp.
Npm устанавливается вместе с node.js, который необходим для загрузки инструментов и библиотек во время разработки.
Платформа Truffle, которую мы будем устанавливать, также должна быть загружена через npm.
Если у вас уже установлены node.js и npm, проверьте версию и пропустите этот раздел, если node.js версии 8 или выше, а npm версии 5 или выше.


Пожалуйста, зайдите на https://nodejs.org и загрузите 10.15.3 LTS. Затем установите его.
Я уже сделал это, и поэтому я пропускаю этот шаг.
После установки мы проверим, правильно ли установлен node.js в PowerShell.
Введите Node-v и проверьте версию. а также проверьте Npm. Npm -v, да, он установлен правильно.


Наконец, я установлю Truffle.
Truffle - это фреймворк, который помогает вам легко развивать BApp.
Truffle позволяет вам компилировать, тестировать и развертывать смарт контракты.
Это очень популярный фреймворк.
Версия Truffle недавно была обновлена до 5.
Однако, поскольку Klaytn был разработан для версии 4, я буду использовать версию Truffle 4.
Если у вас уже установлена версия 4 или менее или 5, сначала необходимо удалить ее.
Удалите ее, введя `npm uninstall -g truffle` в PowerShell.
Теперь вставьте «npm install -g truffle@4.1.15», после установки вы получите версию 4.


Если вы все загрузили, проверьте версию с помощью команды версии Truffle.
Это версия 4.1.15, а компилятор solidity  - версия 0.4.25.
solidity  - это язык программирования, с помощью которого вы можете писать умные контракты. Наконец, давайте загрузим лучший редактор кода,  Visual Studio. Зайдите на https://code.visualstudio.com/ для загрузки под Windows.
Я скачал его заранее. Так что я тоже пропущу эту часть.
Если вы загрузили его, пожалуйста, установите и запустите.
Код Visual Studio поддерживает кроссплатформенность, поэтому работает на Linux, Windows, Mac и включает ряд полезных функций, таких как поддержка отладки, управление git, подсветка синтаксиса и многое другое.




Теперь нажмите на вкладку расширения, чтобы установить расширение для поддержки языка solidity. Пожалуйста, введите «solidity» и выберите тот, что сверху.
Нажмите Установить. Это расширение обеспечивает цветовую подсветку для каждого элемента грамматики solidity и позволяет вам компилировать.
Установка завершена. Я закончил сеанс настройки, который необходим для фронт-энд разработки.
 
 
## 5.2 Скачать шаблон
 
 
Давайте скачаем boiler plate, базовый шаблон для разработки.
Klaytn  говорит, что BApp может быть разработан в рамках Truffle.
 В Truffle есть несколько мест, где вы можете скачать стандартные шаблоны для вашей разработки BApp.
 Это называется Truffle Box.
«Https://truffleframework.com/boxes»
Если Вы зашли по ссылке, Вы можете увидеть шаблоны.
 Например, если вы хотите разработать BApp с использованием Angular или React, вы можете загрузить подходящий вам шаблон.
Однако загруженные здесь шаблоны специализируются на приложении Ethereum, поэтому вам необходимо загрузить их и стереть внутренние части.
 Затем Вы должны настроить шаблон для Klaytn.
Это не сложная часть, но я заранее скачал шаблон под названием webpack
и изменил его «Klaytn way», чтобы вписаться в нашу лекцию.
 Я загрузил его на Github, чтобы вы могли скачать его.
 Для справки, мы продолжим работу с нативным JavaScript и JQuery.
 Даже если вы новичок в этом, вы можете легко следовать за нами
 
Откройте PowerShell и выполните команду git clone в «https://github.com/kkagill/addition-game-starter.git» в том месте, куда вы хотите его скачать.
Я все это уже скачал.
Сделайте «Cd addition-game-starter», чтобы войти в патч. Теперь код. Давайте посмотрим на структуру, вставив «code».
Позвольте мне начать сверху вниз.
В папке «Contracts » хранятся файлы контрактов на solidity
У нас есть файл контракта «Addition Game», который мы создали, и у нас есть контракт под названием «migrations», который позволит вам запускать файлы сценариев в папке миграций ниже, когда вы развертываете свой смарт-контракт.
Это необходимый файл для развертывания контракта, поэтому вы никогда не должны его удалять.
 
Далее, файлы сценариев в папке `migrations` содержат логику, используемую в процессе развертывания.
Если вы видите этот файл, он импортирует файл контракта миграции и развертывает его содержимое на ноде Klaytn.
Внутри папки src я настроил структуру, которая состоит из внешнего интерфейса BApp. Файл index.html будет отвечать за первичное представление.
Я загрузил jquery и bootstrap для использования в BApp вместе с cdn и заранее добавил часть css ниже.
 
Файл Index.js похож на движок - он выполняет функции.
Мы уже определили имена функций, которые мы напишем в будущем.
Переменная внизу - это переменная конфигурации, которая показывает счетчик при загрузке. Это не самая важная часть, поэтому я добавил ее заранее.
В package.json вы добавляете необходимые зависимости через npm.
Важно то, что вы загрузите файл библиотеки, который позволит вам общаться с caver-js, блокчейном Klaytn.
Это похоже на web3 js Ethereum.
Truffle.js отвечает за настройку среды.
Через Truffle вы будете определять, в каких сетях будут внедряться интеллектуальные контракты.
Я расскажу об этом в следующей лекции.
Webpack оптимизирует файлы и обнаруживает изменения в коде и отображает изменения в браузере, не обновляя страницы.
До сих пор я загружал и объяснял стартовый шаблон для создания приложения игры Klaytn BApp.
 



## 5.3 Развертывание смартконтракта на Baobab 1
 
Теперь давайте развернем смартконтракт AdditionGame, который мы формирем в тестовой сети Baobab. Прежде чем мы начнем, мы запустим команду npm install в терминале и установим необходимые зависимости для BApp.
Если вы не видите терминал ниже, выберите новый терминал на вкладке Терминал.
Теперь запустите команду установки npm.
Это займет некоторое время. По завершении создается папка с именем «node_modules» и установка завершается.
 
 
 
Сначала давайте создадим новый файл в папке миграций.
Щелкните правой кнопкой мыши папку «Миграция» и выберите «Новый файл». Установите имя  «2_deploy_contracts.js», и мы добавим логику для развертывания контракта AdditionGame на ноде.
 
Перейдите к файлу `Initial migrations`, скопируйте и вставьте все коды.
Пожалуйста, измените его на «importing the AdditionGame contract».
Замените часть, которая будет развернута, на `AdditionGame`. Пока основная логика для развертывания закончена.
Тем не менее, я напишу определенный код в некоторые файлы в BApp для хранения информации, которую я получаю в процессе развертывания. Позже это может быть очень полезно для создания экземпляров контрактов с этой информацией.
deployer.deploy (AdditionGame)
 
Приложение развертывает контракт AdditionGame, и через `then` мы получаем  данные json.
И в них
 
if (AdditionGame._json) {
 
Если вы получили данные json игры Additions, вы сохраните их в файл через модуль файловой системы.
Чтобы сделать это, вы должны сначала импортировать его.
Добавьте `const fs = require ('fs')` сверху.
Хорошо, тогда я создам два файла. В этих файлах мы можем сохранить Abi и адрес контракта. Щелкните правой кнопкой мыши в любом месте фона и назовите новый файл «deployedABI».
Создайте еще один и назовите его «deployedAddress».
Теперь мы будем использовать файловую систему для хранения их в каждом файле.
Во-первых, давайте создадим код, который хранит информацию abi.
Abi  - это контент, который может взаимодействовать между блокчейном и контрактом.
  	fs.writeFile(
    	'deployedABI',
    	JSON.stringify(AdditionGame._json.abi),
 
В файловой системе есть функция writeFile. Определите, какой файл записать, и зафиксируйте информацию abi, которую мы получили от json, и передайте ее аргументу. Наконец, мы обработаем ошибку.
 
    	(err) => {
      	if (err) throw err
      	console.log("파일에 ABI 입력 성공");
    	})
Если есть ошибка, удалите ее. Если нет, запишите журнал на консоли. Это сохраняет информацию abi развернутого контракта в файле deployedABI как литерал. Для продолжения я сохраню адрес развернутого контракта в файл.
fs.writeFile(
  	'deployedAddress',
  	AdditionGame.address,
  	(err) => {
    	if (err) throw err
    	console.log("파일에 주소 입력 성공");
	})
Если вы уже выполнили все этапы,  мы можем сохранять необходимую информацию в каждом файле сразу после каждого его развертывания. Я продолжу настраивать среду в truffle.js и разверну ее в следующей лекции.
 
 
 
## 5.4 Развертывание смартконтракта на Baobab 2
 
 
Наконец, вам нужно установить настройки. Вы должны решить, какую сеть вы собираетесь развернуть.
Перейдите в файл Truffle.js. Теперь работаем с этого момента. Во-первых, я импортирую библиотеку с именем `connect-privkey-to-provider.`
const PrivateKeyConnector = require ('connect-privkey-to-provider')
 
также создаем константу, называемую идентификатором сети.
 
const NETWORK_ID = '1001'
 
1001 means Baobab's unique network ID.
const GASLIMIT = '20000000'
 
Это предел газа для развертывания. Всего семь нулей.
const URL = `https://api.baobab.klaytn.net:8651`
 
Для UR я назначил адрес, где в настоящий момент работает полная нода Klaytn, в тестнете baobab. Наконец, нам нужна константа для хранения секретного ключа, поэтому мы получим секретный ключ учетной записи, которую мы создали ранее через Klaytn Wallet. Я говорил вам, ребята,  сохранить ваш секретный ключ. Я копирую и вставляю свой, который я сохранил в блокноте.
const PRIVATE_KEY = ''
 
 
Теперь давайте использовать эти настройки в module.exports.
module.exports = {
  networks: { 
	klaytn: {
  	provider: new PrivateKeyConnector(PRIVATE_KEY, URL),
  	network_id: NETWORK_ID,
  	gas: GASLIMIT,
  	gasPrice: null,
	}
  },
}
 
 Позвольте мне объяснить это в первую очередь. Я сказал, что мы будем использовать «Klaytn» для сетей.
Теперь мы укажем четыре варианта. Сначала вы указываете провайдера, который предоставляет узел Klaytn. Создайте экземпляр PrivateKeyConnector и передайте два аргумента.
Первый - передать секретный ключ моей учетной записи, а второй - сетевой адрес, на котором работает полный узел.
Это позволит мне подключиться к тестовой сети баобаба, используя мой секретный ключ.
Присвойте идентификатор сети и газ, и, наконец, цена на газ будет установлена на нулевое значение. Сеть Baobab автоматически установит цену на газ, поэтому мы передаем нулевое значение.
Да, сейчас я настроил свою среду для развертывания смартконтрактов. Это довольно просто. Теперь давайте развернем их. В терминале запустите `truffle deploy -network klaytn`. Да, контракт успешно развернут. Вы можете увидеть фразу подтверждения, в консоли.
 
 
 
Теперь, если вы посмотрите на файл deployedABI, увидите, что информация abi сохраняется. Перейдите к развернутому адресу и обратите внимание, что адрес развернутого контракта сохраняется. Все работает хорошо. Наконец, при развертывании создается папка с именем build. Внутри него есть папка "contracts", а два файла json находятся в папке contracts. Они называются артефактами. Каждый файл артефакта содержит информацию ABI соответствующего контракта, а также всю информацию, связанную с контрактом. ABI - это аббревиатура двоичного интерфейса приложения; мы ранее сохранили развернутый файл ABI в нем. В abi мы видим функции и переменные, записанные в формате json, который мы используем для контракта AdditionGame.
 
Проще говоря, при развертывании этого контракта в блокчейне abi гарантирует вызов функций в контракте и гарантирует, что данные будут возвращены в ожидаемом формате. Именно здесь вы определяете, как вы можете взаимодействовать с контрактом. Если пройти вниз, там есть сетевой раздел. 1001 - уникальный идентификатор сети Klaytn. Этот контракт в настоящее время размещен по этому адресу в тестовой сети Baobab.
 
 
truffle deploy –compile-all –reset –network klaytn
 
 
Наконец, если вы хотите повторно развернуть контракт на узле Klaytn, вы можете использовать эту команду. Например, когда нам нужно изменить договор, нам нужно повторно развернуть его на ноде. `truffle deploy -compile-all -reset -network – Klaytn`
компилировать все, перекомпилировать все контракты. Сброс принудительно запускает файлы сценариев в папке «Миграции». Запустите его, чтобы заново развернуть контракт на узле. Да. Успешно завершено. Откройте файл deployedAddress, и вы увидите, что адрес изменился. Я развернул Контракт в сети Klaytn Baobab, используя truffles.
 
 
 
 
 
## 5.5 Пользовательский интерфейс подтверждения аккаунта
 
 
Начните с входа в свою учетную запись, созданную с помощью кошелька Baobab.
У нас было два способа проверить наши аккаунты.
  Во-первых, вы можете использовать комбинацию файлов и паролей хранилища ключей, а во-вторых, проверить с помощью закрытого ключа.
Мы реализуем это, проверяя комбинацию файлов хранилища ключей и паролей.
Сначала я напишу HTML-код.
Перейдите в Index.html и добавьте фрагмент в тег body.
  <div class="container">
    <div class="row">
  	<div class="col-md-8 col-md-offset-2">
    	<h1 class="text-center">클레이튼(Klaytn)</h1>
    	<h3 class="text-center">속전속결 덧셈 게임</h1>
    	<h3 class="text-center">
      	<code>3초안에 맞출 시 0.1 KLAY 지급 이벤트</code> 
      	<button type="button"
              	class="btn btn-info pull-right"
              	id="login"
              	data-toggle="modal"
              	data-target="#loginModal">
              	로그인
      	</button>
      	<button type="button"
              	class="btn btn-info pull-right"
              	id="logout"
    	          style="display: none;"
              	onclick="App.handleLogout()">
              	로그아웃
      	</button>
    	</h3>        
    	<hr />
  	</div>
	</div>
  </div> 
 
 
 
Пожалуйста, остановите это видео сейчас и напишите этот код.
Очень простая настройка.
Классы в div используют начальную загрузку, чтобы интерфейс выглядел красиво.
 Я пропущу описание начальной загрузки.
Прежде всего, я выложил пояснительные фразы в верхней части.
Ниже мы добавили кнопки входа и выхода.
Когда я нажимаю на кнопку входа, система запускает модальное окно.
Когда я нажимаю кнопку выхода из системы, выполняется функция handleLogout.
Обратите внимание, что я установил кнопку выхода, она не появляется в css.
Давайте запустим приложение, и проверим, работает ли написанный нами код.
Запустите команду npm run dev на терминале.
Запустите Chrome и перейдите по адресу localhost: 8081.
Да, это не так красиво, но выглядит хорошо.
Теперь давайте создадим модальное окно, которое будет появляться при нажатии кнопки входа. ‘Https://bootstrapdocs.com/v3.3.6/docs/javascript/#modals’ Если вы зайдете на сайт начальной загрузки, вы можете получить модальный код.
Скопируйте эту часть и вернитесь в HTML-файл.
Я вставлю это за пределы div.
Теперь давайте изменим содержимое этого фрагмента.
Сначала установите для идентификатора div значение loginModal.
section.
  <div class="modal fade" tabindex="-1" role="dialog" id="loginModal">
 
Вам должно понравиться когда modal открывался при нажатии кнопки входа.
Он соответствует модальному значению атрибута data-target верхней кнопки входа в систему.
Далее мы изменим размер modal на меньший.
 
  <div class="modal-dialog modal-sm">
 
 
Удалить все модальные заголовки раздела.
Также удалите контент внутри модального тела.
Теперь добавьте часть, в которую можно загрузить файл хранилища ключей, и часть, где можно ввести пароль.
<div class="form-group">
   <label for="keystore">Keystore</label>
   <input type="file" id="keystore" onchange="App.handleImport()">
</div>
 
Установите тип ввода как файл и сделайте функцию handleimport для вызова в событии onchange.
  А ниже добавьте часть для пароля (비밀번호). 
 
Скопируйте и вставьте сверху.
<div class="form-group">
  <label for="input-password">비밀번호</label>
  <input type="password" class="form-control" id="input-password" onchange="App.handlePassword()">
   <p class="help-block" id="message"></p>
</div>
 
 
Если значение записано в окне ввода пароля, вызовите функцию handlePassword.
  И я добавил часть, которая будет отображаться в виде сообщения, когда проверка прошла успешно или произошла ошибка.
Наконец, измените`close` на `닫기(close)` и измените `safe changes` на `submission.`
<button type="button" class="btn btn-default" data-dismiss="modal">닫기</button>
        	<button type="button" class="btn btn-primary" id="submit" onclick="App.handleLogin()">제출</button>
 
Добавьте атрибут id и разрешите вызывать функцию handleLogin при нажатии.
Да, сейчас я проверю, что завершенный код работает нормально в приложении.
Нажмите кнопку входа.
Что ж, теперь модал работает, и у вас есть возможность выбрать файл и ввести пароль.
Вот, я создал пользовательский интерфейс для проверки учетных записей.
 
 
## 5.6 Логика проверки аккаунта (проверка хранилища ключей)
 
 
 
Теперь, когда мы создали интерфейс, показанный выше, давайте реализуем логику его работы.
  В Index.js в константе есть различные функции, которые называются App.
И, наконец, когда вы спуститесь вниз, вы увидите, что при загрузке страницы запускается функция запуска, которая существует в константе приложения.
Поэтому мы реализуем функцию start, но перед этим нам нужно загрузить библиотеку caver.js для связи с блокчейном Klaytn и создать ее экземпляр, чтобы ее можно было использовать для BApp.
Импортируйте Caver из "caver-js";
 
Вверху импортируйте caver.js.
Процесс создает одну константу для настройки среды.
 
const config = {
  rpcURL: 'https://api.baobab.klaytn.net:8651'
}
 
 
There’s a rpcURL in config. 
We have defined which Klaytn node to connect to and use. 
I said it is baobab testnet. 
Finally, we will create a constant that instantiates the rpcURL by passing it to the Caver constructor.
const cav = new Caver(config.rpcURL);
 
 
The work of instantiation is over and this cav constant is now available in the app.
 Now you have to start the function, but before that, in the start function, you have to first check whether the account has been verified through the session. 
However, I will leave this part to later because s we will use session in the later lecture, so just leave start function blank for now. 
Let’s implement the handleImport function first.
 We should be able to click on the login button and select the keystore file after modal pops up. 
However, this file must be validated whether it is actually a valid keystore file, or not. 
Let's do that in the handleimport function. 
First, we create a FileReader object and place it into a constant.
const fileReader = new FileReader();
 
 
And use readAsText function to read the selected file.
fileReader.readAsText(event.target.files[0]);
 
 
event.target.files, this part means the file we selected. 
When readAsText execution is completed, the FileReader's onload event occurs.
fileReader.onload = (event) => {  	
  
}
 
The event received by the callback, in other words, the contents of the file, can now be used within this block of code. 
The contents of this file will be checked whether it is a valid keystore file. 
First, add a try catch block inside.
 
  try {
   	
  } catch (event) {
   	
  }
 
 
Now we’ll check through if-sentence if the contents of the file are valid or not, in other words,  if this is an actual keystore file.
if (!this.checkValidKeystore(event.target.result)) {
 
}
 
 
I passed the contents of the file we read to the function checkValidKeystore as an argument.
 Now let's decorate the checkValidKeystore function. 
This function takes the keystore as an argument and receives the file. 
And the keystore file I received is a json file. 
I will change it to Javascript object to use the properties in this json file as variables.
	const parsedKeystore = JSON.parse(keystore);
 
 
I used the json parse function to analyze the contents of the keystore file, convert it to an object, and store it in a constant. 
What should we do next? 
Make sure that the properties required for your keystore configuration are well entered. 
Let's look at the keystore file and see what we need. 
The essential elements of keystore configuration are version, id, address, and crypto. 
Without these four fields, a keystore file can’t be a keystore file. 
So, I will check it through the code.
const isValidKeystore = parsedKeystore.version &&
  	parsedKeystore.id &&
  	parsedKeystore.address &&
  	parsedKeystore.crypto;
 
 
Finally, return this constant.
return isValidKeystore;
 
 
I went up again and verified if the file I just imported is a valid keystore file. 
If not, through message, shows that it is not valid and ends the function.
$('#message').text('유효하지 않은 keystore 파일입니다.');
return;
 
If it passed the verification, then we’ll save the contents of the keystore file to a global variable.
First, we need to create a global variable. Create it on the start function
 
auth: {
	accessType: 'keystore',
	keystore: '',
	password: ''
  },
 
 
There are three fields in the Auth object.
 The accessType is an verification method, which has a keystore type and a privatekey type. 
We are proceeding with keystore type. 
The Keystore field stores the entire contents of the keystore file.
 Lastly, password is the field containing the password that will be combined with the keystore file. 
If we go back to the function and pass the validation,
this.auth.keystore = event.target.result;
 
 
send the entire contents of the loaded file to the keystore field of the auth variable we created. 
After that, send a message saying that I was successful.
$('#message').text('keystore 통과. 비밀번호를 입력하세요.');
 
Make it possible to type password in the password field immediately.
 
document.querySelector('#input-password').focus();
 
Finally, when reading the file, if there is an error, send an error message in the catch block and terminate the function.
$('#message').text('유효하지 않은 keystore 파일입니다.');
return;
 
 
Yes, so far Handleimport function has been implemented well. 
Let's test it now. Select the keystore file. 
The pass message will be displayed and the focus will be moved to the part where the password can be entered. 
To test the opposite case, let’s choose any random file. 
Ok, error message is generated. 
It’s working well. 
Now, let’s make a function that stores the password in a global variable when we enter the password. 
It will be very simple. 
If you go to html, the handlepassword function is called when you enter the password. 
Then, at the handlepassword function,
this.auth.password = event.target.value;
 
Retrieve the password value via the html onchange event and then, assign it to the password field of the global variable auth.
 It was very simple. 
So far, I have done the validation file of the keystore file.
 In the next lecture, I'll create a secret key and add my account information to Wallet.
 
## 5.7 Account verification (integrate wallet)
 

We have completed parts for retrieving the keystore file and the typing password, 
now we will check to see if the account is successfully verified when we send this information to the baobab node. 
Before that, I will replace http in rpcURL to https. 
Take a look at the Index.html. 
When I click submit button, it calls handlelogin function. 
So let’s implement the function. 
First, make sure that the accesstype is a keystore.
if (this.auth.accessType === 'keystore') { 
}

The reason we write this ‘if’ statement is that when verifying an account, we use a keystore or a private key.
We use only keystore for now. 
However, I added these if statements so that when you want to use a private key to verify, 
you can use it. and please add `try catch` statement right below. 
 
 
try {       
} catch (e) 
}

It is time to finally use the caver instance. 
I'll give you a quiz here. 
What can we earn from the combination of the keystore file and password? 
If you remember well, you can know right away. 
Yes, you can get your private key. 
This secret key allows you to create a Wallet instance. 
So the first thing you need to do is to get your secret key through your keystore file and password.
const privateKey = cav.klay.accounts.decrypt(this.auth.keystore, this.auth.password).privateKey;

You can use the decrypt function through the accounts member of the caver instance. 
It means to decrypt. 
If you decrypt it, you can return the decrypted account object by passing the contents of the keystore file and the password as arguments. 
There are various members in the object, and among them, we get the private key and store it in the constant. 
If there is an error in decrypting, a message will be sent.
$('#message').text('비밀번호가 일치하지 않습니다.');
$(‘#message’).text(‘password is not matched.’);
 
If there is no error, it will create a Wallet instance through your secret key.
 
this.integrateWallet(privateKey);



Pass the private key to the integratewallet function. 
Now, go to the integratewallet function. 
Here we add the code that gets the Wallet instance by using privatekey.
 
const walletInstance = cav.klay.accounts.privateKeyToAccount(privateKey);
 

This walletinstance has my account information. 
Then add this instance to my Wallet.
cav.klay.accounts.wallet.add(walletInstance)
 

If you add my account to caver wallet, 
you can easily recall your account information through caver instance when you create a transaction in the future. 
The next step is to store the Wallet instance in the session storage. 
SessionStorage will store the Wallet instance in storage space within the web browser until the tab is closed or the web browser is turned off.
sessionStorage.setItem('walletInstance', JSON.stringify(walletInstance))
 
 

SetItem receives the key value as a pair. 
The first parameter is key and the second parameter is value. 
So, I'll have to load my account information into the session later. 
When you call walletInstance with a key value, the value stored in the pair is automatically loaded.
The reason for using sessionStorage is to keep the account logged in. 
Because my account information stored in my caver wallet disappear when I visit another site or the page refreshes that information. 
However, if you save to session storage, 
your account information will still be maintained even if you visit another site for a while and then return to it or refresh the page. 
So I will implement a Wallet instance session in the start function later and keep it logged in. 
Right now I need to update the UI. 
Now that we have completed account verification via integrateWallet, we need to change the UI appropriately.
this.changeUI(walletInstance);  

I'm sending a Wallet instance to the changeUI function. 
So what do we do with the changeUI function? 
Close your modal.
$('#loginModal').modal('hide');
 

Hide the login button either.
$("#login").hide();
 
Also, change the Logout button that you hid before.
 
$('#logout').show();

And since you are logged in, I want my account address to be visible.
$('#address').append('<br>' + '<p>' + '내 계정 주소: ' + walletInstance.address + '</p>');   
 

This code tells me that it shows the account address in html where the id attribute is address. 
I will go to index.html and add one div.
  <div class="text-center" id="address"></div>    

Yes, you can see my account address at this location. 
I will do it here. 
Now let's test it. 
Click Login button and open the keystore file. 
If you enter your password and press the submit button, your account is verified and the logout button appears. 
Below you can see my account address. 
Finally, let's implement the function to log out. 
Go to Index.html. 
Note that when I click the logout button, I call the handlelogout function. 
I'll go there. 
Here we will call a function called removeWallet.
this.removeWallet();
 

We will clear the wallet and clear the sessionstorage with this function. 
Go to the removeWallet function and add this code.
cav.klay.accounts.wallet.clear();
 
This is the process of erasing my Wallet instance: account information that was added to wallet. 
Then clear the session.
 
sessionStorage.removeItem('walletInstance');

When you’re erasing it, just enter the key value. 
Finally, it calls the reset function and ends.
this.reset();
 

This reset function simply initializes the global variable auth. 
Go to the reset function and initialize auth.
this.auth = {
      keystore: '',
      password: ''
    };
 

There is also an accesstype in Auth. 
But, you don’t have to erase accesstype because it will be a keystore anyway. 
Instead, when we logged in, a value will be entered to the keystore and password fields. 
I want to log out and safely erase it. 
Go back to the handleLogout function and put the code that refreshes the page and finish it. 
The reason for the refresh is to return to the initial state UI.
location.reload();
 

Now let's do the test and finish. 
Clicking the Logout button, the account information will disappear and you are returned to the initialization screen by refreshing. 
Now that you've completed your account verification logic, 
let's complete the section that maintains account verification through session storage in the next class.
 
 
## 5.8 Account Session 

Let's see what happens when we log in and refresh the page. 
Click the login button and select the keystore file. 
In this state, press F5 to refresh. 
Then it’ll be reset. 
It would be good if I kept logged in. 
How do I do it? 
If we succeeded in logging in, we saved the account storage information to the session storage. 
I will use this now. 
The first function that is been loaded when BApp runs is the start function. 
Here I retrieve my account information stored in session storage. 
So, let's go to the start function,
const walletFromSession = sessionStorage.getItem('walletInstance');
 

If you use getItem and pass the value of the key, the value stored in the pair is fetched and stored in the constant. 
I saved my Wallet instance. 
Next, make sure the walletFromSession contains a value.
if (walletFromSession) {
 
}
 

If there is a value, create a try catch.
try { 
     
} catch (e) {
 
  }
 

Then add your account information back to the caver wallet.
cav.klay.accounts.wallet.add(JSON.parse(walletFromSession));

When the page is refreshed or re-visited, the existing account information that was added to Wallet is erased, so I add it back through the session. 
Update the UI to show that you are logged in as next.
  this.changeUI(JSON.parse(walletFromSession));
 

This will turn into a logout button and show me your account address.  
Finally, when the value in sessionStorage is not a valid Wallet instance, it goes to the catch statement. 
Then delete the walletinstance in the session storage.
sessionStorage.removeItem('walletInstance');
 
It’s been done here. 
Now, let’s test it.
When you refresh it, it keeps logged in without returning to the initialization state. 
So far, we have implemented a part of maintaining account verification.
 
 
 
 
## 5.9 KLAY transfer via contract (deposit)
 
 
I will now send the KLAY to the contract using the operator account. 
First, let's create a UI. 
You can create it under the div class row.
 
 
<br />     
 
    <div class="row text-center">
      <div class="col-md-2 col-md-offset-5">
        <div id="owner" style="display: none;">
          <hr />
          <label>컨트랙에 KLAY 보내기</label>
          <div class="input-group">             
            <input type="number" class="form-control" id="amount" />
            <span class="input-group-btn">
              <button type="button" class="btn btn-default" onclick="App.deposit()">송금</button>
            </span>
          </div>
        </div>
      </div>       
    </div>
 

Please fuzz the video and add this part. 
I will explain briefly. 
I have set up the UI part to send money to the contract invisible via css. 
We’ve set the deposit function to run when we enter the amount and press the transfer button. 
Now let's go to the deposit function and implement it. 
 
I will explain here how to implement it first. 
Klay transfer to a contract can only be made with an owner account. 
This is only possible with the account of the person who deployed the Contract. 
In other words, only the organizer of this event can send it. 
If we are using owner account, we will access the deposit function in the contract and transfer the KLAY. 
Flow is very simple. 
First, we will create an instance so that we can access the contract we have deployed. 
When you create a contract instance, you need the abi information and address of the contract you deployed. 
Under the cav constants at the top, 
const agContract = new cav.klay.Contract(DEPLOYED_ABI, DEPLOYED_ADDRESS);

Here deployed_abi and deployed_address are global constants that can be used in BApp. 
Once we deploy the contract, we save information to the deployedabi file and the deployedaddreess file. 
Set it in the webpack so that we can read this information and it use it as a global constant. 
If you go to the Webpack.config.js file, there will be an annotated section. 
Solve this now. 
At compile time in webpacks, run this part to set global constants called deployed address and deployed abi.
 
Simply put, we read the deployedaddress file through the file system and assign the contract address to the global constant. 
In the same way, we store the abi information in global constants which is in deployedabi file. 
Let’s return to the Index.js file.
 
 

So remember that these two abi and address information sent to the creator of the contract instance are passed through the global constants generated by the webpack. 
Now that we've created a four contract instance, we'll continue with the deposit function. 
There’s something we have to check first before sending money. 
You should verify that the account you just signed in is an owner account. 
So I have to bring up two pieces of information. 
First, I'm retrieving the currently logged in account information. 
Second, I’ll retrieve the owner state variable stored in the contract. 
First, I will retrieve my login information.
const walletInstance = this.getWallet();

Go to the getwallet function and get the account information that exists in the current caver wallet.
if (cav.klay.accounts.wallet.length) {
      return cav.klay.accounts.wallet[0];
    }

Wallet [0] is the first account added to Wallet, the account I am currently logged into. 
You’ve finished function implementation so far. 
Next, let's call the value of the owner's state variable in the contract. 
Go to the callOwner function
return await agContract.methods.owner().call();
 

We’ll access the owner function through the additiongame contract instance we created and call the value. 
Use the await keyword to receive values ​​asynchronously. 
Since we made the necessary contents before we send you money, we'll continue with the deposit function.
if (walletInstance) {
 
    }
 

If a Wallet instance exists through the getwallet function, 
compare the current logged in account address with the account address of the owner returned from the contract.
if (await this.callOwner() !== walletInstance.address) return; 
 

If we compare them, but the values ​​are different, we do not proceed anymore and we terminate the function.
 If it is the same
else {
}
 

Gets the value entered for Html input.
var amount = $('#amount').val();

If the input value exists
if (amount) {
}
 
Send the value to the deposit function using a contract instance.
 
agContract.methods.deposit().send({
 
})

Here we send a transaction object as a factor of send. 
We need to specify three things. 
First we have to tell who is calling this function.
from: walletInstance.address,
 
I said that we’ll call this function with the currently logged in account. 
Note that Walletinstance's address is the account that has completed account verification and it has the right to sign the transaction. 
So I can’t put any address in ‘from’. 
Only addresses that have been verified in the BApp can be used as the value. 
And set the gas to be consumed within 250,000.
 
gas: '250000',
 

Since the deposit function in the contract is payable, you must pass the value field.
value:
 

We have to convert the number received from html input to peb which is the minimum unit of KLAY and pass it. 
Convert it by using the utility of caver library.
cav.utils.toPeb(amount, "KLAY")

You can now send money with the contract deposit function. 
But I can use the information that can be received asynchronously, rather than finishing the transaction like this.
.once('transactionHash', (txHash) => {
    console.log(`txHash: ${txHash}`);
})
 

First, I can get the transaction hash, and I made it visible on the console. 
Note that the console log wrapper is not a single quotation mark, but a quotation mark on the left of the number 1. 
Be careful. 
Next, you can get a receipt.
.once('receipt', (receipt) => {
   console.log(`(#${receipt.blockNumber})`, receipt);          
})

Getting a receipt means that the transaction was successfully added to the block. 
So, you can check the receipt to see the block where the transaction was added. 
If transaction processing fails, you might get an error.
.once('error', (error) => {
   alert(error.message);
  }); 
 

If there is an error, a message will be display. 
I've done the logic to check success after sending the transaction. 
Finally, if there is no amount received in html input, add a return statement that terminates the function.
return;
 

I have completed the part that sends the KLAY to the deposit function of contract, and I will change the UI and test it in the next class. 
 
 
## 5.10 KLAY transfer via contract (UI change and testing)
 
 

I will try changing UI and testing. 
When we sent a KLAY to the deposit function in the previous course and received a receipt, the transaction was successful. 
What should I do after I succeeded? 
It would be nice if the system could show me the reminder message.
   alert(amount + " KLAY를 컨트랙에 송금했습니다.");  
 

And I will refresh the page to see the balance of the contract.
   location.reload();     
.

I said that I’m going to make the balance of the contract visible. 
Remember that we created a function that would load the contract's balance when we wrote the smart contract. 
We will call this getBalance function so we can see the balance of the contract. 
First, we'll add a div that displays the contract's balance in html. 
Go to Index.html and add one div under the address that shows my account address.
  <div class="text-center" id="contractBalance"></div>

And then we'll show you the balance of the contract here. 
Now that the view is ready, let's create a function that loads the balance from the backend. 
Go to the callcountractbalance function and add the code.
return await agContract.methods.getBalance().call();
 

The part that accesses the getbalance function through a contract instance and loads the value. Yes, it was simple. 
Where do I call this callcountractbalance function from now? 
Where should I call it? 
If the transaction succeeds in the deposit function and receives a receipt, it refreshes the page via location.reload (). 
What is the first function that executes when the page is refreshed? 
The start function is executed first. 
Then, we call the changeUI function from the start function. 
I need to add code to load the contract balance from the changeUI function that changes UI immediately.
$('#contractBalance').append('<p>' + '이벤트 잔액: ' + cav.utils.fromPeb(await this.callContractBalance(), "KLAY") + ' KLAY' + '</p>');     

It's a bit long. 
I’ll explain. 
We will add a message to the part that shows the contract balance In html. 
Call the callContractBalance function to get the balance. 
However, the balance is then loaded into the KLAY minimum unit, peb. 
That would make it hard to see how much is left in the user's seat, because the unit is too big. 
So the caver utility has a function called fromPeb.
It is a function that can convert from peb to another unit. 
I have specified in the second parameter to convert to KLAY. 
As a result, it shows the contract balance converted into KLAY in html.
 

Lastly, the KLAY transfer to the contract must be set up only for the owner account. 
You only have to give permission to the event organizer. 
So I will change it to show the UI that can be transferred only when I log in with the owner account. Go to the changeUI function
if (await this.callOwner() === walletInstance.address) {
      $("#owner").show(); 
    }     
 
I have set the owner div to show only when the owner account address and the logged in account address are the same. 
In html, the owner div is set invisible by default.
So, when you log in with the owner account, you will see this part.
Now let's try testing. 
I will re-deploy it once. 
First, make sure that your account's secret key is properly entered in truffle.js. 
I will re-ploy it from the terminal.
‘truffle deploy -compile-all -reset -network klaytn’ I'm re-deploying it for people who have not deployed it. 
Your deployment is over. 
Let's check it by running npm run dev. Press F12 to open the console window. 
Click Login button
Since you are logged in with your owner account, you can see the part where you can send money. 
Let's send money now. Send 1 KLAY.
 
 

You can see the transaction hash and receipt information through the console log as your transaction succeeds. 
The notification message works well. 
It seems that the time required for the transaction was less than 3 seconds. 
In these 3 seconds, there are four processes from creating the transaction to creating the block and propagating it to the network when the transaction is completed. 
Compared to other block-chain platforms, the processing speed is very fast. 
Click the notification message, the page refreshes, and the start function is called first, 
and the updated contract balance is displayed by the changeUI function in it. 
The transaction function is working well. 
I'd like to have a load spinner shows that the transaction works well or not. 
This is not a requirement, but I recommend you to do it for a good UI. 
Go to Index.js and import spin.js to the top.
import {Spinner} from 'spin.js';

Go to the showspinner function and make it return the spinner instance.
var target = document.getElementById('spin');
    return new Spinner(opts).spin(target);

And call this function from the deposit function.
var spinner = this.showSpinner();
 
After receiving a receipt, make the spinner stop.
 
  spinner.stop();  

Finally, add a div to show the spinner in html. <br /> Make it under the tag.
<div id="spin"></div>    
 

Now let's try testing. 
Yes. As the spinner comes out, a more spectacular scene is being produced. 
The transfer function works well, and the UI is well reflected. 
So far, I have covered the KLAY transfer from the owner account to the contract.

## 5.11Generating a random number

Now let 's try to make an interesting part. 
Let's create two random numbers to be used for addition. 
I will decorate Html first. 
Please add this code directly above the spin div.
<div class="row text-center">
        <div id="game" style="display: none;">   
          <div class="yellow-box" id="start">       
            <a href="#" onclick="App.generateNumbers()">시작</a>
          </div>     
          <div class="yellow-box" id="question" style="display: none;">
            <span id="num1"></span> + <span id="num2"></span> = ?          
            <div class="input-group">
              <input type="number" class="form-control" id="answer" />
              <span class="input-group-btn">
                <button type="button" class="btn btn-default" onclick="App.submitAnswer()">제출</button>
              </span>
            </div>
          </div>     
        </div> 
      </div>
<br />
 

I made it invisible with the css. 
And I’ll make it visible after I log in. 
Clicking on the start button calls the generateNumbers function. 
The function will then generate two numbers, one for the num1 and one for num2. 
To be used for addition. 
And there is an input field to write the answer. 
Finally, there is a button to submit your answers. 
Simple html. Now, 
I'll set it up so that only users who have been verified will see this part. 
Go to the changeUI function and add it below logout.show () to show the game div.
$('#game').show();
 

Now let's check it out in html. 
If you are logged in, you can see the nice UI of the yellow box in the middle. 
Now I’ll set the numbers visible when you click on Start. 
Let's create random numbers in the generatenumbers function.
var num1 = Math.random();
 

First, we call the random function of the Math class. 
The random function randomly generates a number with a decimal point below 0 and 1. 
But if you do this, the number is too small, so I'm going to multiply it.
var num1 = Math.random() * 50;
 

This will generate a random number from 0 to 49. 
But the problem should not be too easy, so I will add 10 to the generated value so that you can generate at least two digits.
var num1 = (Math.random() * 50) + 10;
 

Finally, we use the floor function to discard the decimal point.
var num1 = Math.floor((Math.random() * 50) + 10);
 
If you do this, you will have a decimal number between 10 and 59.
Next, create another one.
 
var num2 = Math.floor((Math.random() * 50) + 10);
 
Now we will store the added values of two numbers ​​in the session storage. 
I'll save the answer.
 
sessionStorage.setItem('result', num1 + num2);    

This will later bring the correct answer back when the user answers and will try to compare the answers given by the user. 
Now that we've created the numbers, we'll have to use it. 
When I click on Start in html, I will hide this beginning and make it show the question div below. And at the same time, I will make the two numbers generated from the function visible in the num1 and num2 fields. 
Let's go back to the function and implement what we just said.
$('#start').hide();
 

Make the beginning invisible.
$('#num1').text(num1);
$('#num2').text(num2);

Let it show the generated numbers in num1 and num2 fields. 
And let it show the question div.
$('#question').show(); 
	

Finally, move the focus to where I write the answers so that I can answer right away.
document.querySelector('#answer').focus();

I will test it now. 
When you click Start, your random numbers are generated and rendered in html. 
Soon, focus moved to where I write the answer. 
This is the end of today’s class and I will try to create a timer in the next class.

## 5.12  Generating a timer



Let's create a timer and set the timeout for the addition problem to 3 seconds.
 Go to Html and make a div that shows the timer. I'll make it right under the spin div.
<div class="row text-center">
        <p id="timer"></p>
      </div>   
 
Go to index.js and go to the showtimer function. Here we use the setInterval function to show the number to be counted down. We’ll make the problem disappear after 3 seconds and the screen revert back to the start click.
 

Make a variable to save for 3 seconds.
$('#timer').text(seconds);

Show number 3 directly to the html which is showing the timer. 
I use the setinterval function and set it at 1 second interval.
  var interval = setInterval(function() {  
  }, 1000);
 

Now I can run something in 1 second interval.
$('#timer').text(--seconds);  
 

Decrement the number one by one to make it appear in html. 
Now, the value of this seconds variable is 0, that is, reset it again when setinterval is 0 after 3 seconds.
if (seconds <= 0) {
}     
 
When Seconds becomes 0
 
$('#timer').text('');
 

Initialize the number showing part
     $('#answer').val('');
답적었던input도 초기화시키구요	

Also initialize the input that was answered.
$('#question').hide();
 
Set the div not showing the problem. And,
 
$('#start').show();          
 

Show the div again that you can click start. Finally,
  clearInterval(interval);
 

Use the clearInterval to stop the time running in setinterval. Yes, I have created the showtimer function. Now let's call this function in the generateNumbers function.
this.showTimer();
 
If you do this, as soon as you click Start, the timer will be created and count down will be started. Let's try testing.
Click on Start. A timer will be generated below and start the count down for 3 seconds. After 3 seconds, it is reset again.
So far, I have created a timer.
 
 
 
## 5.13 Submitting answers and receiving KLAY
 
This is the last class. If the user submits the answer and the answer is correct, let's implement the part that sends the KLAY to the user account from the contract. Go to the submitAnswer function. Load the value of correct answer which is stored in the session storage.
const result = sessionStorage.getItem('result');
 

And, store the answers that the user has made in the variables.
var answer = $('#answer').val();  
 

Now, do a comparison.
if (answer === result) { }
 

If the user has answered the correct answer, press the confirm button while opening the confirm message window and send the KLAY to the user.
if (confirm("대단하네요^^ 0.1 KLAY 받기")) { }
 

If the user clicked the OK button, make sure the balance in the contract is at least 0.1 KLAY before sending it.
if (await this.callContractBalance() >= 0.1) { }

If so, call the receiveKlay function.
this.receiveKlay();
 

If it does not exist, send a notification message.
else { alert("죄송합니다. 컨트랙의 KLAY가 다 소모되었습니다."); }    
 

Finally, if the user did not get the correct answer, Send a notification.
else { alert("땡! 초등학생도 하는데 ㅠㅠ"); }
 
 
 

Yes your submitanswer function is up to here. 
Let's test it once. 
This message is displayed when the answer is wrong. 
When this is done, a confirm message window will appear to receive the KLAY. 
When you click OK, you will call the receiveklay function to transfer the KLAY. 
I have not implemented it yet. 
Let's implement the function. 
It's our last function.
 
When the user answers the correct answer, they pay the transaction fee through their account and get the KLAY. 
We will convert 0.1 KLAY in our contract transfer function to peb and pass it as an argument. 
First, let's show you how to load using a spinner during transaction processing.
var spinner = this.showSpinner();

In addition, we need the verified account address required for the transaction, so, load the Wallet instance.
const walletInstance = this.getWallet();
 

If the value of the wallet instance does not exist, exit the function.
if (!walletInstance) return;  
 

If so, use the contract instance to access the transfer function in the contract .
agContract.methods.transfer().send({
})
 
The transfer function of the contract receives one argument. 
You need use the caver utility to convert the KLAY to peb and pass it. 
 
cav.utils.toPeb(“0.1”, "KLAY")
 
And you said you need to send a transaction object in the send parameter. 
You need to specify who calls this function and how much the gas limit is set.
 
from: walletInstance.address,
gas: '250000'
 
Pass the Wallet instance, your account-verified address, and let the gas consume within 250,000. 
Note that the value field is not required. 
I will not pass the value because the transfer function is not a payable type. 
If you do this, you have finished all the values which will be passed. 
Now, after the transaction is processed, you should check whether it succeeded or not. 
I could check whether it(deposit) succeeded or not through this .once. 
However, there’s another way. 
I can get a receipt by using promise.
 
.then(function (receipt) {
});     

Wait asynchronously and receive the receipt value.
if (receipt.status) { }

There is a field called status in the Receipt object. 
If this is true, it is successful. 
So, if you succeed, Stop spinner.
spinner.stop(); 
 

Also, show notification messages
alert("0.1 KLAY가 " + walletInstance.address + " 계정으로 지급되었습니다.");      
 

Also, let's create a link in html so that the processed transaction can be checked directly from the scope. 
I'm going to create a new div. 
I will make it under the timer div.
<div class="row text-center">
   <div id="transaction"></div>
</div>  

<br />
 

You'll see the link in this section. 
Go back to the function and clear the transaction div first.
    $('#transaction').html("");
 

I’m clearing the transaction div to show a new link each time a transaction is created. 
Next, I'll add a link.
    $('#transaction')
      .append(`<p><a href='https://baobab.klaytnscope.com/tx/${receipt.txHash}' 
                   target='_blank'>클레이튼 Scope에서 트랜젝션 확인</a></p>`);
 
 
In the receipt returned by the promise, 
pass the transactionhash field to the url parameter of the KlaytnScope site so that you can see the transaction information just processed. 
Lastly, show you the last updated contract balance in html.
 
return agContract.methods.getBalance().call()
  .then(function (balance) {
});        
 
Call the getBalance function of the contract to recall the remaining balance in the contract.
 
 $('#contractBalance').html("");          
 

Clears the existing show balance display and shows the updated balance immediately.
$('#contractBalance').append('<p>' + '이벤트 잔액: ' + cav.utils.fromPeb(balance, "KLAY") + ' KLAY' + '</p>');           
 
The whole process is complete so far. 
Now, let's try testing. 
This time, I try to log in with a different account, not the owner account. 
You can continue with the owner account. 
If you have created another account, you can try it out as well.
 
If you solve the problem and press the OK button, the receiveKlay function is called. 
The notification message is displayed and the transaction has been successfully completed. 
You can close the notification message and see that your event balance is reduced. 
The balance in the contract has been reduced as it moves to your account. 
And the link was created at the bottom. 
If you click the link, you can see the information about the track we just created on the scope. 
Click on your account address and you'll see that the balance is growing. 
So far, I have tried to solve the problem and transfer the KLAY in the contract to my account.
