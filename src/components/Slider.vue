<template>
  <div class="page">
    <h1 class="primary-title centered">Мои работы</h1>
    <p class="centered">
        Описание применных в проекте технологий откроется по наведению мыши на слайд
    </p>
    <div class="slideshow-container centered">
      <div class="slider-wrapper">
          <Slide
            v-for="(slide, index) in slides"
            :key="slide['btn-img-class']"
            :slide="slide"
            :index="index"
            :activeSlide="activeIndex"
          />
      </div>
        <div class="btn-prev" id="btn-prev" @click="showPrevSlide"></div>
        <div class="btn-next" id="btn-next" @click="showNextSlide"></div>
    </div>
    <div class="dots-wrapper">
      <span
        v-for="(item, index) in slides"
        :key="item"
        :class="['dot', {'active': index === activeIndex}]"
        @click="showSlide(index)"
        ref="dot"
      />
    </div>
  </div>
  <div class='project-materials'>
    <ul class='no-list-type'>
      <li
        v-for="(item, index) in slides"
        :key="item"
        :class="{'hidden': index !== activeIndex}"
      >
        <a
          class='btn'
          v-if="item.links.site"
          :href="item.links.site"
        >
          Cайт
        </a>
        <a
          class='btn'
          v-if="item.links.github"
          :href="item.links.github"
        >
          Github
        </a>
        <a
          class='btn'
          v-if="item.links.other"
          :href="item.links.other.address"
        >
          {{ item.links.other.name }}
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
import Slide from '@/components/Slide.vue';

export default {
  name: 'Slider',
  components: {
    Slide,
  },
  data() {
    return {
      // * отвечает за показ нужного слайда
      activeIndex: 0,
      slides: [
        {
          'btn-img-class': 'tutoring',
          'btn-info-class': 'tutoring-info',
          title: 'Vue 3, c сентября 2021.',
          description: {
            text: 'интерактивное приложение для частного репетиторства',
          },
          skills: [
            'SCSS',
            'Проверка пользовательского ввода',
            'Однофайловые компоненты, слоты, пропсы и т.д',
            'Vue router',
            'Vue draggable',
            'БЭМ',
            'Heroku deploy',
          ],
          links: {
            site: 'https://daria-blomma-tutoring.herokuapp.com',
            github: 'https://github.com/DariaBlomma/tutoring-vue',
          },
        },
        // {
        //   'btn-img-class': 'ozon-task-3',
        //   'btn-info-class': 'ozon-task-3-info',
        //   title: 'Vue 2, ноябрь 2021.',
        //   description: {
        //     text: 'карта офиса',
        //   },
        //   skills: [
        //     'Vue 2',
        //     'SVG loader',
        //   ],
        //   links: {
        //     github: 'https://github.com/ozon-edu-vue-2021/required-task-3-DariaBlomma',
        //   },
        // },
        {
          'btn-img-class': 'formMedods',
          'btn-info-class': 'formMedods-info',
          title: 'Vue 3, июнь 2021.',
          skills: [
            'Sass',
            'Vuelidate 2',
            'валидация полей при вводе, при blur, показ ошибок пользователю',
            'адаптивная верстка',
          ],
          links: {
            site: 'https://dariablomma.github.io/form_medods/',
            github: 'https://github.com/DariaBlomma/form_medods',
          },
        },
        {
          'btn-img-class': 'simonGame',
          'btn-info-class': 'simonGame-info',
          title: 'Vue 3, июнь 2021.',
          description: {
            list: [
              'Игровое поле состоят из 4 квадратов / кнопок, каждый из которых производит определенный тон и «загорается» при нажатии.',
              'Раунд в игре состоит из устройства, освещающего одну или несколько кнопок в случайном порядке. После чего игрок должен воспроизвести этот порядок, нажимая кнопки.',
              'Если игрок успешно воспроизводит последовательность, то они переходят к следующему раунду.',
              'Если игрок не воспроизводит последовательность, то игра окончена (уведомление должно  отображаться для пользователя).',
              'С каждым раундом количество кнопок (последовательность) увеличивается.',
            ],
          },
          skills: [
            'Sass',
            'Vuelidate 2',
            'валидация полей при вводе, при blur, показ ошибок пользователю',
            'адаптивная верстка',
          ],
          links: {
            site: 'https://dariablomma.github.io/simon-game/',
            github: 'https://github.com/DariaBlomma/simon-game',
          },
        },
        {
          'btn-img-class': 'insane',
          'btn-info-class': 'insane-info',
          title: 'JavaScript, май 2021.',
          hasBigList: true,
          skills: [
            'валидация данных формы с помощью регулярных выражений',
            'отправка данных формы на сервер с помощью fetch',
            'разные виды слайдеров - со счетчиком, с больше чем 1 слайдом за раз, с изменяющимся поведением стрелочек, слайдеры в попапе',
            'разное открытие меню в зависимости от ширины экрана',
            'многочисленные попапы, по нажатию или наведению мыши',
            'информация в мод. окне "Полный список услуг и цен" берется из базы данных',
            'плавная прокрутка по нажатию на ссылки в меню, кнопке "Вверх"',
            'аккордеон - раздел Часто задаваемые вопросы',
            'использование коллекций Map, Set',
            'использование ООП для создания слайдеров',
            'админка, а именно:',
            'запрет перехода на страницу личного кабинета без успешной авторизации (проверка через кукис)',
            'вход, простая валидация формы, показ сообщения о неправильно введенном логине или пароле (логин и пароль: admin)',
            'автоматический переход на следующую страницу при успешной авторизации',
            'данные на следующей странице берутся с АПИ - для опций раскрывающегося списка, для информации в таблице',
            'возможность редактировать данные, удалять, добавлять новые (методы patch, delete, post)',
            'сборка webpack',
          ],
          links: {
            site: 'https://dariablomma.github.io/insane-diploma/src/layout/',
            github: 'https://github.com/DariaBlomma/insane-diploma',
            other: {
              name: 'админка',
              address: 'https://dariablomma.github.io/insane-diploma/src/layout/admin/',
            },
          },
        },
        {
          'btn-img-class': 'glo3d',
          'btn-info-class': 'glo3d-info',
          title: 'JavaScript, апрель - май 2021.',
          skills: [
            'таймер обратного отсчета',
            'RAF анимации - открытие и закрытие меню, попапа Оставить заявку',
            'валидация полей с помощью регулярных выражений',
            'отправка данных из формы на сервер',
            'табы в разделе Наши услуги',
            'автоматический слайдер с пагинацией',
            'анимация бегущих цифр в калькуляторе Рассчитать стоимость',
            'слайдер карусель в разделе Нам доверяют',
            'работа с дата атрибутами для смены картинки по наведению мыши в разделе Наша команда',
            'сборка webpack',
          ],
          links: {
            site: 'https://dariablomma.github.io/3dglo/',
            github: 'https://github.com/DariaBlomma/3dglo',
          },
        },
        {
          'btn-img-class': 'glo-project1',
          'btn-info-class': 'glo-project1-info',
          title: 'JavaScript, апрель 2021.',
          skills: [
            'написание приложения в ООП стиле',
            'валидация полей с помощью регулярных выражений',
            'добавление полей на странице по нажатию кнопки',
            'сброс калькулятора к исходному состоянию',
            'вычисления бюджета из введенных данных и вывод в другие инпуты на странице',
            'работа с атрибутом disabled',
            'обработка данных с инпута range - вывод числа под инпутом, перерасчет бюджета при изменении',
            'работа с массивами, строками для сохранения и вывода данных',
          ],
          links: {
            site: 'https://dariablomma.github.io/GloAcademy.18.0/Project%201/Obligatory%20tasks/',
            github: 'https://github.com/DariaBlomma/GloAcademy.18.0',
          },
        },
        {
          'btn-img-class': 'scandi',
          'btn-info-class': 'scandi-info',
          title: 'Верстка, март 2021.',
          skills: [
            'верстка по макету из Фигма',
            'применение grid, flexbox',
            'попытка следовать БЭМ-методологии',
            'проверено на html валидаторе, на переполнение',
            'простая валидация формы c помощью js на соответствие pattern',
          ],
          links: {
            site: 'https://dariablomma.github.io/HTMLAcademy.-Marathon-3.0/',
            github: 'https://github.com/DariaBlomma/HTMLAcademy.-Marathon-3.0',
            other: {
              name: 'макет',
              adress: 'https://www.figma.com/file/MTtAmzLAzCsMHDsEwTBgLg/Марафон-3.0?node-id=1%3A2',
            },
          },
        },
        {
          'btn-img-class': 'logitech',
          'btn-info-class': 'logitech-info',
          title: 'Верстка, февраль-март 2021.',
          skills: [
            'верстка по макету из Фигма',
            'адаптивная верстка mobiles-first с помощью медиа запросов',
            'адаптивное гамбургер-меню на js',
            'автоматические слайдеры, останавливаются по наведению мыши',
            'применение grid для элементов на текущем слайде',
          ],
          links: {
            site: 'https://dariablomma.github.io/logitech/',
            github: 'https://github.com/DariaBlomma/logitech',
            other: {
              name: 'макет',
              adress: 'https://www.figma.com/file/YIt8h03frNCF6AbJnFFAvY/Logitech_MX-Master-3-(Copy)-(Copy)-(Copy)?node-id=211%3A144',
            },
          },
        },
        {
          'btn-img-class': 'your-house',
          'btn-info-class': 'your-house-info',
          title: 'Верстка, осень 2020.',
          skills: [
            'flexbox',
            'верстка по макету Photoshop',
            'фильтр по таблице на js на странице staff.html',
            'раскрывающиеся списки на "Подобрать персонал", "Оставить заявку", "Подобрать персонал"',
            'линейные градиенты в меню',
          ],
          links: {
            site: 'https://dariablomma.github.io/your-house/main_page.html',
            github: 'https://github.com/DariaBlomma/your-house',
            other: {
              name: 'макет',
              address: 'https://mega.nz/folder/ijgyXJaY#RuPNvSa6skdYSMTReSASmQ',
            },
          },
        },
        {
          'btn-img-class': 'summer-trip',
          'btn-info-class': 'summer-trip-info',
          title: 'Верстка, лето 2020.',
          skills: [
            'адаптивная верстка на первой странице с помощью медиа запросов',
            'php на страницах challenge',
          ],
          links: {
            github: 'https://github.com/DariaBlomma/summer-trips',
          },
        },
        {
          'btn-img-class': 'odysseum',
          'btn-info-class': 'odysseum-info',
          title: 'Макеты, ноябрь 2020.',
          skills: [
            'навыки работы в Фигма на примере странички магазина',
          ],
          links: {
            other: {
              name: 'макет',
              address: 'https://www.figma.com/file/5x09vTmuMaxHx6PNY3Rc69/Page3.-Design.Odysseum',
            },
          },
        },
        {
          'btn-img-class': 'photoshop',
          'btn-info-class': 'photoshop-info',
          title: 'Макеты, декабрь 2020.',
          skills: [
            'навыки работы в Photoshop на примере landing page',
          ],
          links: {
            other: {
              name: 'макет',
              address: 'https://www.dropbox.com/s/ezb68rhsbiusrgi/min%20swedish.psd?dl=0',
            },
          },
        },
      ],
    };
  },
  methods: {
    showPrevSlide() {
      if (this.activeIndex === 0) {
        this.activeIndex = this.slides.length - 1;
      } else {
        this.activeIndex--;
      }
    },
    showNextSlide() {
      if (this.activeIndex === this.slides.length - 1) {
        this.activeIndex = 0;
      } else {
        this.activeIndex++;
      }
    },
    showSlide(number) {
      this.activeIndex = number;
    },
    showProjectInfo(link) {
      window.location.href = link;
    },
  },
};
</script>
