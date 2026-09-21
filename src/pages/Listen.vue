<template>
  <div class="listen-page">
    <Header />
    <main class="listen-hero" :ref="setSectionRef(0)">
      <Transition name="fade-collapse">
      <div v-show="!expandedSections[0]" class="listen-inner" style="width:1366px; height:751px; margin:0 auto; position:relative;">
        <img class="text-left text_1" src="../assets/images/home/text_1.png" alt="text" />
        <div class="main-content-box">
          <img src="../assets/images/home/img_8.png" class="list-icon" alt="list" />
          <ul class="mc-list">
            <li>Different experiences of young and experienced inheritors;</li>
            <li>How to study and comprehend "Manas";</li>
            <li>Why do oral performances change;</li>
            <li>Digital media communication;<br>What makes "Manas" a "living tradition".</li>
          </ul>
        </div>

        <div class="people-column">
          <div class="person-row">
            <div class="avatar" />
            <div class="name-group">
              <div class="name">Tokom &amp; Suyundouke</div>
            </div>
          </div>
        </div>

        <div class="down-indicator" @click="toggleExpand(0)">
          <img src="../assets/images/home/icon-arrow.png" alt="down" />
        </div>
      </div>
      </Transition>
      <!-- Expandable content for section 1 -->
      <Transition name="fade-expand">
      <div v-if="expandedSections[0]" class="expand-content">
        <img class="text-left text_1" src="../assets/images/home/text_1.png" alt="text" />

        <!-- Part 1: Suyundouke - A Childhood Built Around Manas -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-name">Suyundouke:</span>
            <span class="expand-subtitle">A Childhood Built Around Manas</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
          <h3 class="expand-title"><img src="../assets/images/home/img_9.png" class="title-icon" alt="star" /> Summary</h3>
          <p class="expand-desc">Suyundouke began learning Manas when he was about ten years old. As a child, he was so interested in the epic that he would secretly read it during class, even when his teacher tried to stop him. During school breaks, he performed parts of Manas for his classmates. After listening, his classmates would give him blank sheets of paper, and his mother would sew them together into a handmade notebook. Support from his mother, classmates, and teachers made Manas a strong part of his childhood and encouraged him to keep learning and performing it.</p>
          <h3 class="expand-title"><img src="../assets/images/home/img_10.png" class="title-icon" alt="dots" /> Edric Commentary</h3>
          <p class="expand-desc">I used to imagine cultural transmission as something formal, with an older expert teaching a younger student. Suyundouke's story made me see it differently. It showed me that transmission can begin in a very small community. A family, a group of classmates, and one child who wants to keep telling the story can already form a small network that helps a tradition continue.</p>
        </div>

        <!-- Part 2: Suyundouke - A Book Can Preserve Manas -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-name">Suyundouke:</span>
            <span class="expand-subtitle">A Book Can Preserve Manas. A Performer Makes It Alive.</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
          <h3 class="expand-title"><img src="../assets/images/home/img_9.png" class="title-icon" alt="star" /> Summary</h3>
          <p class="expand-desc">Suyundouke explains that written texts have helped preserve Manas more completely, especially parts that might otherwise be lost through oral transmission. But for many Manaschis, the version recorded in a book is still a "static" Manas. The epic becomes "living" through performance, when a Manaschi uses voice, rhythm, facial expressions, eye contact, and movement to bring emotion into the story and connect with the audience.</p>
          <h3 class="expand-title"><img src="../assets/images/home/img_10.png" class="title-icon" alt="dots" /> Edric Commentary</h3>
          <p class="expand-desc">I used to think that writing down an oral epic was one of the clearest ways to preserve it. Suyundouke made that idea more complicated for me. A written text can preserve the words, but it cannot fully preserve the experience of hearing them performed. Voice, emotion, rhythm, and movement are not simply additions to the story. They are part of what makes the tradition alive.</p>
        </div>

        <!-- Part 3: Tokom - Bringing Manas Into the Digital Age -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-name">Tokom:</span>
            <span class="expand-subtitle">Bringing Manas Into the Digital Age</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
          <h3 class="expand-title"><img src="../assets/images/home/img_9.png" class="title-icon" alt="star" /> Summary</h3>
          <p class="expand-desc">Tokom describes how his relationship with Manas developed from memorization in childhood to deeper study, writing, and eventually digital media. Since 2022, he has used platforms such as Douyin, WeChat Channels, and Kuaishou to share performances, stories, and explanations of the epic. Because Manas is often too long for short-form platforms, he divides longer performances into smaller sections. For him, digital transmission means adjusting the form of the tradition so that it can fit the habits and attention of today's audiences.</p>
          <h3 class="expand-title"><img src="../assets/images/home/img_10.png" class="title-icon" alt="dots" /> Edric Commentary</h3>
          <p class="expand-desc">I used to think that bringing a tradition online simply meant giving more people access to it. Tokom made me notice that the platform itself can also change how a tradition is presented. A story that once unfolded through a long live performance may now be divided into several short videos. The content can remain connected to the same tradition, while the form changes for a different audience. It made me think about adaptation not only as a way to reach more people, but as part of how a tradition continues in a new media environment.</p>
        </div>

        <!-- Part 4: Tokom - Memorizing Is Not the Same as Understanding -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-name">Tokom:</span>
            <span class="expand-subtitle">Memorizing Is Not the Same as Understanding</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
          <h3 class="expand-title"><img src="../assets/images/home/img_9.png" class="title-icon" alt="star" /> Summary</h3>
          <p class="expand-desc">Tokom explains that passing on Manas requires much more than memorization. After learning the text, he believes a Manaschi must understand it, study it, and reorganize it before sharing it with others. He has read Manas six or seven times since childhood and still feels there are parts he does not fully understand. For him, the epic is almost like an entire field of study, containing history, customs, culture, and knowledge from different communities.</p>
          <h3 class="expand-title"><img src="../assets/images/home/img_10.png" class="title-icon" alt="dots" /> Edric Commentary</h3>
          <p class="expand-desc">I often thought of memorization as one of the main signs that someone had truly learned a tradition. Tokom made me see that memory is only the beginning. Understanding, research, and interpretation are also part of transmission. What interested me most is that passing something on does not mean repeating it exactly. It means doing enough work with the material that you can make sense of it and help someone else understand it too.</p>
        </div>

        <!-- Part 5: Tokom - The Same Story Is Never Told Exactly the Same Way -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-name">Tokom:</span>
            <span class="expand-subtitle">The Same Story Is Never Told Exactly the Same Way</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
          <h3 class="expand-title"><img src="../assets/images/home/img_9.png" class="title-icon" alt="star" /> Summary</h3>
          <p class="expand-desc">Tokom describes Manas as a "living epic" because the same story is never performed in exactly the same way. A Manaschi may change the tone, rhythm, gestures, wording, or level of detail depending on the setting, the audience, and the performer's own state. Even so, the main structure and storyline remain consistent. This balance between continuity and improvisation is part of what allows Manas to stay alive as an oral tradition.</p>
          <h3 class="expand-title"><img src="../assets/images/home/img_10.png" class="title-icon" alt="dots" /> Edric Commentary</h3>
          <p class="expand-desc">I often thought of preservation as keeping something unchanged, but Tokom's explanation suggests a different idea. Manas stays recognizable because its core story remains, even while each performance can change. That made me think more carefully about the line between retelling and changing a tradition. Maybe the question is not whether change happens, but which parts can change without losing what makes the tradition itself.</p>
        </div>

        <div class="collapse-indicator" @click="toggleExpand(0)">
          <img src="../assets/images/home/icon-arrow.png" alt="up" class="arrow-up" />
        </div>
      </div>
      </Transition>
    </main>
    <!-- Second section: same layout, alt background and content -->
    <main class="listen-hero alt" :ref="setSectionRef(1)">
      <Transition name="fade-collapse">
      <div v-show="!expandedSections[1]" class="listen-inner" style="width:1366px; height:751px; margin:0 auto; position:relative;">
        <img class="text-left text_2" src="../assets/images/home/text_2.png" alt="text2" />
        <div class="main-content-box">
          <img src="../assets/images/home/img_8.png" class="list-icon" alt="list" />
          <h4 class="mc-subtitle">Performance / Audience Perspective</h4>
          <ul class="mc-list">
            <li>Personal stories behind musicians and their instruments;</li>
            <li>How to introduce young audiences to unfamiliar traditions.</li>
          </ul>
          <h4 class="mc-subtitle">Academic / Research Perspective</h4>
          <ul class="mc-list">
            <li>Preservation vs. Development;</li>
            <li>How to understand different music systems;</li>
            <li>Ethnic music and field research methods.</li>
          </ul>
        </div>

        <div class="people-column">
          <div class="person-row">
            <div class="avatar avatar-2" />
            <div class="name-group">
              <div class="name">买迪娜 &amp; 吐尔洪教授</div>
            </div>
          </div>
        </div>

        <div class="down-indicator" @click="toggleExpand(1)">
          <img src="../assets/images/home/icon-arrow.png" alt="down" />
        </div>
      </div>
      </Transition>
      <Transition name="fade-expand">
      <div v-if="expandedSections[1]" class="expand-content">
        <img class="text-left text_2" src="../assets/images/home/text_2.png" alt="text2" />

        <!-- Part 1: 吐尔洪教授 -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-name">吐尔洪教授:</span>
            <span class="expand-subtitle">How Do You Preserve a Tradition Without Freezing It?</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
          <h3 class="expand-title"><img src="../assets/images/home/img_9.png" class="title-icon" alt="star" /> Summary</h3>
          <p class="expand-desc">Professor Turhong describes preservation and development as a balance rather than a choice between two extremes. He believes important parts of a tradition should be protected, but the ways it is presented may need to change as younger audiences and media habits change. Using Xinjiang folk music as an example, he explains how new arrangements, new languages, and online platforms can help unfamiliar audiences enter a tradition. For him, the goal is not simply to tell young people that a tradition is valuable, but to help them understand why it matters.</p>
          <h3 class="expand-title"><img src="../assets/images/home/img_10.png" class="title-icon" alt="dots" /> Edric Commentary</h3>
          <p class="expand-desc">I often think the hardest question is not whether a tradition should change, but how far that change can go. Professor Turhong's answer made me think about adaptation as a question of access and boundaries at the same time. A new format can help more people enter a tradition, but it should not erase the features that make the tradition distinct. That balance seems to be one of the central challenges of keeping cultural traditions meaningful today.</p>
        </div>

        <!-- Part 2: 买迪娜 -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-name">买迪娜:</span>
            <span class="expand-subtitle">How Do You Make a Tradition Meaningful to a Child?</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
          <h3 class="expand-title"><img src="../assets/images/home/img_9.png" class="title-icon" alt="star" /> Summary</h3>
          <p class="expand-desc">Madina explains that young children do not need to begin by memorizing names, history, or musical terms. She suggests letting them watch and listen first, then asking what they noticed. Their own observations can become the starting point for learning about the performers, instruments, stories, and history behind the Twelve Muqam. For her, curiosity should come before explanation, so that children first connect with the experience and then gradually understand what they saw.</p>
          <h3 class="expand-title"><img src="../assets/images/home/img_10.png" class="title-icon" alt="dots" /> Edric Commentary</h3>
          <p class="expand-desc">I often assumed that understanding had to come before interest. Madina's approach made me think about the order differently. Someone new to a tradition may first need a detail that catches their attention, such as a sound, an instrument, a person, or a story. That small moment of curiosity can become the beginning of deeper learning. It made me realize that making a tradition accessible does not always mean simplifying it. Sometimes it means giving people the right place to enter.</p>
        </div>

        <div class="collapse-indicator" @click="toggleExpand(1)">
          <img src="../assets/images/home/icon-arrow.png" alt="up" class="arrow-up" />
        </div>
      </div>
      </Transition>
    </main>
    <!-- Third section: same layout as second, white background, different content -->
    <main class="listen-hero" :ref="setSectionRef(2)">
      <Transition name="fade-collapse">
      <div v-show="!expandedSections[2]" class="listen-inner" style="width:1366px; height:751px; margin:0 auto; position:relative;">
        <img class="text-left text_3" src="../assets/images/home/text_3.png" alt="text3" />
        <div class="main-content-box">
          <img src="../assets/images/home/img_8.png" class="list-icon" alt="list" />
          <ul class="mc-list">
            <li>Tradition and Adaptation;</li>
            <li>What can be changed;</li>
            <li>What needs to be retained;</li>
            <li>Traditional vs. Adapted Performance</li>
          </ul>
        </div>

        <div class="people-column">
          <div class="person-row">
            <div class="avatar" />
            <div class="name-group">
              <div class="name">尼玛</div>
            </div>
          </div>
        </div>

        <div class="down-indicator" @click="toggleExpand(2)">
          <img src="../assets/images/home/icon-arrow.png" alt="down" />
        </div>
      </div>
      </Transition>
      <Transition name="fade-expand">
      <div v-if="expandedSections[2]" class="expand-content">
        <img class="text-left text_3" src="../assets/images/home/text_3.png" alt="text3" />

        <!-- Part 1: 尼玛 -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-name">尼玛:</span>
            <span class="expand-subtitle">Tradition Has to Change to Stay Alive</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
          <h3 class="expand-title"><img src="../assets/images/home/img_9.png" class="title-icon" alt="star" /> Summary</h3>
          <p class="expand-desc">Nima explains that Jangar has never remained completely unchanged because it has been passed down orally for generations. While details may shift, the main story and core ideas remain. Since around 2012, he and other performers have experimented with new ways of presenting the epic by shortening long sections, rearranging the music, adding instruments, and using throat singing. For Nima, these changes do not replace the original story. They help the tradition reach contemporary audiences while keeping its core recognizable.</p>
          <h3 class="expand-title"><img src="../assets/images/home/img_10.png" class="title-icon" alt="dots" /> Edric Commentary</h3>
          <p class="expand-desc">I often thought of innovation and preservation as two opposite directions. Nima's approach made that distinction feel less simple. The real challenge seems to be deciding what must remain recognizable and what can change with the audience and the time. A tradition does not have to stay in exactly the same form to remain itself. In some cases, changing the way it is presented may be what allows its core story to keep being heard.</p>
        </div>

        <!-- Part 2: Traditional vs Adapted Performance -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-subtitle">Traditional vs Adapted Performance</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
        </div>

        <div class="collapse-indicator" @click="toggleExpand(2)">
          <img src="../assets/images/home/icon-arrow.png" alt="up" class="arrow-up" />
        </div>
      </div>
      </Transition>
    </main>
    <!-- Fourth section: alt background, different left image and person -->
    <main class="listen-hero alt" :ref="setSectionRef(3)">
      <Transition name="fade-collapse">
      <div v-show="!expandedSections[3]" class="listen-inner" style="width:1366px; height:751px; margin:0 auto; position:relative;">
        <img class="text-left text_4" src="../assets/images/home/text_4.png" alt="text4" />
        <div class="main-content-box">
          <img src="../assets/images/home/img_8.png" class="list-icon" alt="list" />
          <ul class="mc-list">
            <li>Oral instruction;</li>
            <li>Learn sentence by sentence;</li>
            <li>Transmission among students;</li>
            <li>Performance Practice;</li>
            <li>Voice, body, clothing, and emotion.</li>
          </ul>
        </div>

        <div class="people-column">
          <div class="person-row">
            <div class="avatar avatar-2" />
            <div class="name-group">
              <div class="name">乌图那生</div>
            </div>
          </div>
        </div>

        <div class="down-indicator" @click="toggleExpand(3)">
          <img src="../assets/images/home/icon-arrow.png" alt="down" />
        </div>
      </div>
      </Transition>
      <Transition name="fade-expand">
      <div v-if="expandedSections[3]" class="expand-content">
        <img class="text-left text_4" src="../assets/images/home/text_4.png" alt="text4" />

        <!-- Part 1: 乌图那生1 -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-name">乌图那生:</span>
            <span class="expand-subtitle">Teaching One Line at a Time</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
          <h3 class="expand-title"><img src="../assets/images/home/img_9.png" class="title-icon" alt="star" /> Summary</h3>
          <p class="expand-desc">Wutunasheng explains that Mongolian Long Song can still be taught without formal music theory or written notation. He learned the tradition orally and now teaches his students in much the same way, guiding them through the melody and lyrics one line at a time. Students who read staff or numbered notation can use it as an additional tool, while others continue to learn by listening and repeating. Students who learn quickly may also help teach their classmates, creating another layer of transmission within the group.</p>
          <h3 class="expand-title"><img src="../assets/images/home/img_10.png" class="title-icon" alt="dots" /> Edric Commentary</h3>
          <p class="expand-desc">I often assumed that writing music down would naturally make it easier to teach. What I saw here was more flexible. Notation can help, but the tradition does not depend on it. Listening, repetition, and learning directly from another person still remain at the center of the process. I was especially interested in how students can become teachers themselves, so transmission does not move in only one direction.</p>
        </div>

        <!-- Part 2: 乌图那生2 -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-name">乌图那生:</span>
            <span class="expand-subtitle">A Performance Is More Than Singing the Right Notes</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
          <h3 class="expand-title"><img src="../assets/images/home/img_9.png" class="title-icon" alt="star" /> Summary</h3>
          <p class="expand-desc">Wutunasheng explains that a strong Long Song performance is judged by more than vocal technique. Posture, stage presence, traditional clothing, confidence, and emotional expression all contribute to the performance as a whole. He believes a song should feel connected from beginning to end and should be sung sincerely enough to move the audience. That confidence on stage, he adds, comes from regular practice and long-term preparation.</p>
          <h3 class="expand-title"><img src="../assets/images/home/img_10.png" class="title-icon" alt="dots" /> Edric Commentary</h3>
          <p class="expand-desc">I was used to thinking about musical performance mainly in terms of how accurately someone played or sang. Wutunasheng described something much broader. Voice, body, clothing, confidence, and emotion all belong to the performance together. It made me realize that what is being passed on is not simply a set of correct notes, but an entire way of performing and communicating with an audience.</p>
        </div>

        <div class="collapse-indicator" @click="toggleExpand(3)">
          <img src="../assets/images/home/icon-arrow.png" alt="up" class="arrow-up" />
        </div>
      </div>
      </Transition>
    </main>
    <!-- Fifth section: same layout as fourth, alt background -->
    <main class="listen-hero" :ref="setSectionRef(4)">
      <Transition name="fade-collapse">
      <div v-show="!expandedSections[4]" class="listen-inner" style="width:1366px; height:751px; margin:0 auto; position:relative;">
        <img class="text-left text_5" src="../assets/images/home/text_5.png" alt="text5" />
        <div class="main-content-box">
          <img src="../assets/images/home/img_8.png" class="list-icon" alt="list" />
          <ul class="mc-list">
            <li>Improvisation;</li>
            <li>Dombra;</li>
            <li>Real-time Response;</li>
            <li>Humor / Competition;</li>
            <li>Audience Interaction.</li>
          </ul>
        </div>

        <div class="people-column">
          <div class="person-row">
            <div class="avatar avatar-3" />
            <div class="name-group">
              <div class="name">MORE</div>
            </div>
          </div>
        </div>

        <div class="down-indicator" @click="toggleExpand(4)">
          <img src="../assets/images/home/icon-arrow.png" alt="down" />
        </div>
      </div>
      </Transition>
      <Transition name="fade-expand">
      <div v-if="expandedSections[4]" class="expand-content">
        <img class="text-left text_5" src="../assets/images/home/text_5.png" alt="text5" />

        <!-- Part 1: Listen, Think, Answer -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-name">阿肯:</span>
            <span class="expand-subtitle">Listen, Think, Answer — All in Real Time</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
          <h3 class="expand-title"><img src="../assets/images/home/img_9.png" class="title-icon" alt="star" /> Summary</h3>
          <p class="expand-desc">Aqyn Aitys is a form of live poetic exchange rather than a rehearsed song. Two performers listen to each other, think quickly, and respond immediately through improvised lyrics, melody, and dombra playing. Each Aqyn develops a personal vocal style and chooses melodic patterns that fit their own voice. The exchange can be competitive, humorous, or playful, but it always depends on the ability to turn thought into poetry and music in real time.</p>
          <h3 class="expand-title"><img src="../assets/images/home/img_10.png" class="title-icon" alt="dots" /> Edric Commentary</h3>
          <p class="expand-desc">What interested me most was how many things have to happen at the same time. An Aqyn has to listen carefully, understand the other person, think of a response, shape it into poetry, and sing it with music almost immediately. It made me see improvisation as much more than spontaneity. It depends on language, memory, musical skill, and a large amount of knowledge already built up before the performance begins.</p>
        </div>

        <!-- Part 2: The Art of the Comeback -->
        <div class="expand-block">
          <div class="expand-header">
            <span class="expand-name">男女对唱:</span>
            <span class="expand-subtitle">The Art of the Comeback</span>
          </div>
          <div class="howto-video">
            <div class="video-placeholder">
              <div class="play-circle">
                <img src="../assets/images/home/icon-play.png" alt="play" />
              </div>
            </div>
          </div>
          <h3 class="expand-title"><img src="../assets/images/home/img_9.png" class="title-icon" alt="star" /> Summary</h3>
          <p class="expand-desc">Humor is an important part of Aqyn Aitys. Performers do not simply take turns singing. They tease, joke, challenge each other, and react to what is happening in the moment. In male-female duets, this can become especially playful, with compliments, witty replies, and verbal sparring built into the exchange. Audience reaction also matters. Laughter and attention become part of the performance and help shape its rhythm and energy.</p>
          <h3 class="expand-title"><img src="../assets/images/home/img_10.png" class="title-icon" alt="dots" /> Edric Commentary</h3>
          <p class="expand-desc">I used to think of improvisation mainly as the ability to create something quickly. Aitys showed me that timing and audience response matter just as much. A good comeback has to be clever, musical, and immediate, but it also has to land with the people listening. That made me realize that this tradition is not only a conversation between two performers. It is also a conversation with the audience.</p>
        </div>

        <div class="collapse-indicator" @click="toggleExpand(4)">
          <img src="../assets/images/home/icon-arrow.png" alt="up" class="arrow-up" />
        </div>
      </div>
      </Transition>
    </main>
    <!-- Sixth section: interview card -->
    <main class="listen-hero alt interview-section">
      <div class="interview-card">
        <div class="interview-titles">
          <h2>Keeping Oral Traditions Alive:</h2>
          <h3>Language, Change, and</h3>
          <h3>the Future of Cultural Transmission</h3>
        </div>
        <div class="interview-info">
          <p><strong>采访者：</strong> Dan Wang is a professor at Xinjiang Arts University whose research focuses on Kazakh traditional music, oral performance, and related cultural traditions in Xinjiang. Her work includes areas such as Aqyn Aitys and other forms of Kazakh musical and oral culture. In this interview, she discusses the preservation of oral traditions, language and translation, digital media, and the challenges of cultural transmission today.</p>
        </div>
        <a href="#/listen-detail" class="interview-arrow" @click="scrollToTop">
          <img src="../assets/images/home/icon-arrow2.png" alt="go" />
        </a>
      </div>
    </main>
    <Footer />
  </div>
</template>

<script setup>
import { reactive, ref, nextTick } from 'vue'
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'

const expandedSections = reactive([false, false, false, false, false])
const sectionRefs = ref([])

const setSectionRef = (index) => (el) => {
  if (el) sectionRefs.value[index] = el
}

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

const toggleExpand = (index) => {
  const isOpen = expandedSections[index]
  const scrollY = window.scrollY
  for (let i = 0; i < expandedSections.length; i++) {
    expandedSections[i] = false
  }
  if (!isOpen) {
    expandedSections[index] = true
    nextTick(() => {
      window.scrollTo(0, scrollY)
    })
  } else {
    nextTick(() => {
      const el = sectionRefs.value[index]
      if (el) {
        el.scrollIntoView({ behavior: 'smooth', block: 'start' })
      }
    })
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/scss/_var.scss';

.listen-hero {
  background-color: #fff;
  position: relative;
  padding-bottom: 40px;
}

.text-left {
  position: absolute;
  left: 0;
  top: 20px;

  height: auto;
}

.text_1{
  width: 129px;
}
.text_2{
  width: 128px;
}
.text_3{
  width: 124px;
}
.text_4{
  width: 71px;
}
.text_5{
  width: 126px;
}
.listen-hero.alt {
  background-image: url('../assets/images/home/bg4.png');
  background-repeat: no-repeat;
  background-position: center top;
  background-size: cover;
  padding-bottom: 40px;
}

.avatar.avatar-2 {
  background-image: url('../assets/images/home/person_2.png');
  background-size: cover;
  background-position: center;
}

.avatar.avatar-3 {
  background-image: url('../assets/images/home/person_3.png');
  background-size: cover;
  background-position: center;
}

.listen-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 751px;
  position: relative;
}

.main-content-box {
  width: 640px;
  margin-left: 220px;
}
.list-icon {
  width: 48px;
  height: auto;
  margin-bottom: 20px;
  display: block;
}
.mc-subtitle {
  font-size: 20px;
  font-style: italic;
  font-weight: 700;
  color: #111;
  margin-bottom: 12px;
}
.mc-list {
  list-style: none;
  padding: 0;
  margin: 0 0 24px;
  li {
    font-size: 20px;
    line-height: 1.6;
    color: #111;
    margin-bottom: 8px;
    padding-left: 20px;
    position: relative;
    &::before {
      content: '●';
      position: absolute;
      left: 0;
      color: #111;
    }
  }
}

.people-column {
  width: 280px;
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
  margin-right: 80px;
}

.person-row {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.avatar {
  width: 375px;
  height: 420px;
  background-color: #aec3bc;
  background-size: cover;
  background-position: center;
  border-radius: 8px;
  margin: 0 auto 16px;
}

.name-group {
  text-align: center;
}

.name {
  font-family: $font-serif;
  font-size: 18px;
}

.down-indicator {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  bottom: 24px;
  cursor: pointer;
}
.down-indicator img {
  width: 48px;
  height: 48px;
  opacity: 0.9;
  transition: transform 0.3s ease;
}
.down-indicator img.arrow-up {
  transform: rotate(180deg);
}

/* Expand content area */
.expand-content {
  position: relative;
  max-width: 1366px;
  padding: 60px 0;
  text-align: center;
  margin: 0 auto;
}

.expand-block {
  margin-bottom: 60px;
}

.expand-header {
  text-align: left;
  padding: 0 200px;
  margin-bottom: 24px;
}
.expand-name {
  font-size: 22px;
  font-weight: 700;
  color: #854529;
  margin-right: 8px;
}
.expand-subtitle {
  font-size: 16px;
  font-weight: 400;
  color: #111;
}

.expand-title {
  font-family: $font-serif;
  font-size: 26px;
  font-weight: 700;
  color: #0e0a06;
  margin: 0 0 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}
.title-icon {
  width: 30px;
  height: 30px;
  display: inline-block;
  vertical-align: middle;
}

.expand-desc {
  font-size: 15px;
  color: #333;
  font-style: normal;
  line-height: 1.85;
  margin-bottom: 40px;
  max-width: 680px;
  margin-left: auto;
  margin-right: auto;
  text-align: center;
}

.collapse-indicator {
  cursor: pointer;
  display: flex;
  justify-content: center;
  margin-top: 20px;

  img {
    width: 48px;
    height: 48px;
    opacity: 0.9;
    transition: transform 0.3s ease;
  }
  img.arrow-up {
    transform: rotate(180deg);
  }
}
.howto-video {
  display: flex;
  justify-content: center;
  margin-bottom: 36px;
}
.video-placeholder {
  width: 960px;
  height: 480px;
  background: #aec3bc;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 4px;
  position: relative;
}
.play-circle {
  width: 86px;
  height: 86px;
  border-radius: 50%;
}
.play-circle img {
  width: 100%;
  height:  100%;
}
/* Interview card section */
.interview-section {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 700px;
  padding: 80px 0;
}
.interview-card {
  width: 680px;
  background-color: #aec3bc;
  border-radius: 20px;
  padding: 60px 50px 50px;
  position: relative;
}
.interview-titles {
  margin-bottom: 60px;
  h2 {
    font-size: 28px;
    font-weight: 700;
    color: #111;
    margin: 0 0 4px;
    line-height: 1.4;
  }
  h3 {
    font-size: 22px;
    font-weight: 400;
    color: #111;
    margin: 0;
    line-height: 1.4;
  }
}
.interview-info {
  p {
    font-size: 14px;
    line-height: 1.8;
    color: #222;
    margin: 0;
  }
  strong {
    font-weight: 700;
  }
}
.interview-arrow {
  position: absolute;
  right: 30px;
  bottom: 30px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  img {
    width: 40px;
    height: 40px;
    opacity: 0.8;
    transition: opacity 0.3s;
  }
  &:hover img {
    opacity: 1;
  }
}

@media (max-width: 1200px) {
  .listen-inner { width: 100%; padding: 0 20px; box-sizing: border-box; }
  .text-left { display: none; }
  .main-content-box { width: 60%; margin-left: 20px; }
  .people-column { display: none; }
}
</style>

<style lang="scss">
/* Transition animations - must be unscoped for Vue Transition to work */
.fade-collapse-enter-active,
.fade-collapse-leave-active {
  transition: opacity 0.4s ease, max-height 0.5s ease;
  overflow: hidden;
}
.fade-collapse-enter-from,
.fade-collapse-leave-to {
  opacity: 0;
  max-height: 0 !important;
  overflow: hidden;
}
.fade-collapse-enter-to,
.fade-collapse-leave-from {
  opacity: 1;
  max-height: 800px;
}

.fade-expand-enter-active {
  transition: opacity 0.5s ease 0.15s, transform 0.5s ease 0.15s;
}
.fade-expand-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}
.fade-expand-enter-from {
  opacity: 0;
  transform: translateY(-20px);
}
.fade-expand-enter-to {
  opacity: 1;
  transform: translateY(0);
}
.fade-expand-leave-from {
  opacity: 1;
  transform: translateY(0);
}
.fade-expand-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}
</style>

