# file-C-Users-stud543-Desktop-D0-AF-D1-81-D1-8B-D1-80-D0-B5-D0-B2-geolyceum2025-index.html
git clone https://github.com/zayarniy/geolyceum2025.git

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>География 2025. Столицы</title>

    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css">
    <link rel="stylesheet" href="styles.css">
    <script src="libs/vue@2.js"></script>
    <script src="libs/speaker.js" defer></script>
    <script src="data.js"></script>

    
</head>

<body>
    <div id="app" class="containter">
        <div class="row lh-1 text-center align-middle" style="color:black">
            <table class="table text-center caption-top thead-light table-striped">
                <tbody>
                    <thead>
                        <tr>
                            <td class="infoLabel"></td>
                            <td class="infoLabel"></td>
                            <td class="infoLabel"></td>
                            <td class="infoLabel">Баллов</td>
                        </tr>
                    </thead>
                    <tr class="info">
                        <td><button class="btn btn-primary" @click="startGame" id="startGame">Запустить</button></td>
                        <td><button class="btn btn-secondary mr-2" @click="nextQuestion" :disabled="!gameOn">Следующая</button></td>
                        <td><button class="btn btn-warning" @click="restartGame">С начала</button></td>
                        <td><span id="countAttempts" class="score">{{score}}</span>
                        </td>
                    </tr>
                </tbody>
            </table>
            <table>
                <tr>
                    <td><button class="btn btn-primary" style="width: 100px;" @click="addScore(+1)" :disabled="!gameOn" id="addScore">+1</button></td>
                    <td><button class="btn btn-primary" style="width: 100px;" @click="addScore(0)" :disabled="!gameOn" id="addScore">0</button></td>
                    <td><button  class="btn btn-primary" style="width: 100px;" @click="addScore(-1)" :disabled="!gameOn" id="removeScore">-1</button></td>
                </tr>
            </table>
        </div>        
        <div class="row">
            <div class="col-8">
                <timer  class="main-timer" ref="mainTimer" :time="timerTime" @timeout="handleTimeout('mainTimer')"></timer>
            </div>
            <div class="col-4">
                <timer class="add-timer" ref="addTimer" :time="addTimerTime" @timeout="handleTimeout('addTimer')"></timer>
                <h3 class="text-center">Стран:{{countries.length}}</h3>
                <div v-if="selectedContinents.length > 0">
                    <h3>Выбранные континенты:</h3>
                    <ul class="two-column-list">
                        <li v-for="selected in selectedContinents" :key="selected">{{ selected }}</li>
                    </ul>
                </div>
            </div>
            
        </div>
        <div class="row text-center mt-5">
            <div class="col country">
                {{country}}
            </div>
        </div>
        <div class="row">
                <div class="col capital text-center" @click="showCapital" v-show="isCapitalShow">
                    {{capital}}
    
            </div>


        </div>
    <div class="hint-container text-center" style="font-size: small;">
        <div class="hint-toggle" onclick="toggleHint()">Настройки</div>
        <div class="hint-content" style="text-align: justify;">
            <h6>Настройки</h6>
            <div>
                <label for="gameTime">Время на игру (сек)</label>
                <input type="number" v-model="timerTime" id="gameTime" placeholder="Время игры в секундах">
                <label for="addTimer">Время на ответ (сек)</label>
                <input type="number" v-model="addTimerTime" id="addTimer" placeholder="время на ответ в секундах">
                <label for="isNext">Автоматический переход</label>
                <input type="checkbox" v-model="isNext">
                <label for="isNext">Озвучка</label>
                <input type="checkbox" v-model="isSpeak">
                <h6>Континенты:</h6>
        <label v-for="continent in continents" :key="continent">
            <input type="checkbox" v-model="selectedContinents" :value="continent">
            {{ continent }}
        </label>
        <div><strong>Смена континентов учитывается при запуске игры</strong></div>
            </div>
            </div>
        </div>


    </div>
</div>

    <script src="libs/script.js" defer></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
</body>

</html>

