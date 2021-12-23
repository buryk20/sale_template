<template>
  <div class="promo-template">
    <section class="promo-template__wrp-bun">
        <div class="promo-template__img-back">
            <img
            class="promo-template__img"
            src="/image/cyber_monday_artboard.png"
            alt="Акционное предложение"
            />
        </div>
        <div class="promo-template__text">
            <div class="promo-template__text-img-wrp">
                <div class="promo-template__text-pos">
                    <h1 class="promo-template__text-title">
                        Экстра лимитированое предложение!<span
                        class="promo-template__text-star"
                        >*</span
                        >
                    </h1>
                    <div class="promo-template-counter">
                        <div class="promo-template-counter__wrp">
                        <div class="promo-template-counter__wrp-number">
                            <p class="promo-template-counter__number">{{ days }}</p>
                            <p>Day</p>
                        </div>
                        </div>
                        <div class="promo-template-counter__colon">:</div>
                        <div class="promo-template-counter__wrp">
                        <div class="promo-template-counter__wrp-number">
                            <p class="promo-template-counter__number">{{ hours }}</p>
                            <p>Hour</p>
                        </div>
                        </div>
                        <div class="promo-template-counter__colon">:</div>
                        <div class="promo-template-counter__wrp">
                        <div class="promo-template-counter__wrp-number">
                            <p class="promo-template-counter__number">{{ minutes }}</p>
                            <p>Minutes</p>
                        </div>
                        </div>
                        <div class="promo-template-counter__colon">:</div>
                        <div class="promo-template-counter__wrp">
                        <div class="promo-template-counter__wrp-number">
                            <p class="promo-template-counter__number">{{ seconds }}</p>
                            <p>Seconds</p>
                        </div>
                        </div>
                    </div>
                    <div class="promo-template__text-main">
                        <p>
                        Черная пятница с GreenVision – не упустите свой шанс купить
                        систему видеонаблюдения по низкой цене. В период с 22 по 30 ноября
                        2021 года каждый покупатель получает скидку 25% на весь
                        ассортимент товаров GreenVision Черная пятница Черная пятница с
                        GreenVision – не упустите свой шанс купить В период с 22 по 30
                        ноября 2021 года каждый покупатель получает скидку 25% на весь
                        ассортимент товаров GreenVision*
                        </p>
                    </div>
                    <button class="promo-template-counter__btn"><a href="#">Подробнее</a></button>
                </div>
                <div class="promo-template__img-width-wrp">
                    <img class="promo-template__img-width" src="/image/cyber_monday_img.png" alt="Скидка">
                </div>
            </div>
        </div>
    </section>
  </div>
</template>

<script>
export default {
    name: "promoTemp",
    data() {
        return {
            deadline: 'January 1 2022 00:00:00 GMT+0300',
            days: '00',
            hours: '00',
            minutes: '00',
            seconds: '00',
            expired: false
        };
    },
    methods: {
        theTime(){
        var ctx = this;
            // Цикл обратного отсчета
            var x = setInterval(function(){
                //Разница между двумя датами
                var countDownDate = new Date(ctx.deadline).getTime(),
                now = new Date().getTime(),
                diff = countDownDate - now,
                // Преобразование времени в дни, часы, минуты и секунды
                tdays = Math.floor(diff / (1000 * 60 * 60 * 24)),
                thours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)),
                tminutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60)),
                tseconds = Math.floor((diff % (1000 * 60)) / 1000);
                // Отображать две цифры
                ctx.days = (tdays < 10) ? '0' + tdays : tdays;
                console.log(ctx.days);
                ctx.hours = (thours < 10) ? '0' + thours : thours;
                ctx.minutes = (tminutes < 10) ? '0' + tminutes : tminutes;
                ctx.seconds = (tseconds < 10) ? '0' + tseconds : tseconds;
                // Проверка истечения времени
                if(diff < 0){
                clearInterval(x);
                ctx.expired = true;
                }
            }, 1000);
            // Возвращение данных
            return {
            days: ctx.days,
            hours: ctx.hours,
            minutes: ctx.minutes,
            seconds: ctx.seconds
            };
        }
    },
    beforeMount() {
        this.theTime()
    }
};
</script>

<style lang="scss" src="../../public/scss/main_prom_temp.scss" scoped></style>
