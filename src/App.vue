<script>
import DChatMessage from '@/components/chat/ChatMessage'

const avatar = 'https://images.unsplash.com/photo-1590031905470-a1a1feacbb0b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144'

export default {
  name: 'App',

  components: { DChatMessage },

  data () {
    return {
      message: '',
      chat: [
        {
          date: new Date(),
          avatar: 'https://images.unsplash.com/photo-1549078642-b2ba4bda0cdb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144',
          messages: [
            { text: 'Can be verified on any platform using docker' }
          ]
        },
        {
          date: new Date(),
          avatar: 'https://images.unsplash.com/photo-1590031905470-a1a1feacbb0b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144',
          messages: [
            { text: 'Your error message says permission denied, npm global installs must be given root privileges.' }
          ],
          sent: true
        },
        {
          date: new Date(),
          avatar: 'https://images.unsplash.com/photo-1549078642-b2ba4bda0cdb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144',
          messages: [
            { text: 'Command was run with root privileges. I\'m sure about that.' },
            { text: 'I\'ve update the description so it\'s more obviously now' },
            { text: 'FYI https://askubuntu.com/a/700266/510172' },
            { text: 'Check the line above (it ends with a # so, I\'m running it as root ) <pre># npm install -g @vue/devtools</pre>' }
          ]
        },
        {
          date: new Date(),
          avatar: 'https://images.unsplash.com/photo-1590031905470-a1a1feacbb0b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144',
          messages: [
            { text: 'Any updates on this issue? I\'m getting the same error when trying to install devtools. Thanks' }
          ],
          sent: true
        },
        {
          date: new Date(),
          avatar: 'https://images.unsplash.com/photo-1549078642-b2ba4bda0cdb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144',
          messages: [
            { text: 'Thanks for your message David. I thought I\'m alone with this issue. Please, 👍 the issue to support it :)' }
          ]
        },
        {
          date: new Date(),
          avatar: 'https://images.unsplash.com/photo-1590031905470-a1a1feacbb0b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144',
          messages: [
            { text: 'Are you using sudo?' },
            { text: 'Run this command sudo chown -R `whoami` /Users/{{your_user_profile}}/.npm-global/ then install the package globally without using sudo' }
          ],
          sent: true
        },
        {
          date: new Date(),
          avatar: 'https://images.unsplash.com/photo-1549078642-b2ba4bda0cdb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144',
          messages: [
            { text: 'It seems like you are from Mac OS world. There is no /Users/ folder on linux 😄' },
            { text: 'I have no issue with any other packages installed with root permission globally.' }
          ]
        },
        {
          date: new Date(),
          avatar: 'https://images.unsplash.com/photo-1590031905470-a1a1feacbb0b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144',
          messages: [
            { text: 'yes, I have a mac. I never had issues with root permission as well, but this helped me to solve the problem' }
          ],
          sent: true
        },
        {
          date: new Date(),
          avatar: 'https://images.unsplash.com/photo-1549078642-b2ba4bda0cdb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144',
          messages: [
            { text: 'I get the same error on Arch Linux (also with sudo)' },
            { text: 'I also have this issue, Here is what I was doing until now: #1076' },
            { text: 'even i am facing' }
          ]
        }
      ]
    }
  },

  mounted () {
    this.lastMessages()
  },

  methods: {
    sent () {
      const chat = this.chat[this.chat.length - 1]

      // mock
      if (chat.avatar !== avatar) {
        this.chat.push({
          avatar: avatar,
          messages: [{
            text: this.message
          }],
          sent: true
        })
      } else {
        chat.messages.push({ text: this.message })
      }

      this.message = null

      this.$nextTick(() => {
        this.lastMessages()
      })
    },
    lastMessages () {
      const container = this.$refs.messages
      container.scrollTop = container.scrollHeight
    }
  }
}
</script>

<template>
  <div id="app" class="flex h-screen font-sans">
    <div class="hidden sm:block w-1/5 bg-gray-200 px-4 pt-6">
      <div class="flex items-center space-x-4">
        <img class="w-12 h-12 rounded-full" src="https://images.unsplash.com/photo-1590031905470-a1a1feacbb0b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144" alt="My profile">
        <div class="flex flex-1 flex-col leading-tight">
          <span class="text-lg font-semibold text-blue-600">David Henrique</span>
          <span class="text-xs text-gray-600">Senior Develop</span>
        </div>
        <button type="button" class="block inline-flex items-center justify-center rounded-full h-10 w-10 transition duration-500 ease-in-out text-gray-600 hover:bg-gray-300" >
          <svg class="h-5 w-5" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z" />
          </svg>
        </button>
      </div>
      <div class="relative mt-6 flex">
        <span class="absolute inset-y-0 pl-4 flex items-center">
          <svg class="h-4 w-4 text-gray-400" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
          </svg>
        </span>
        <input type="text" class="py-2 pl-10 rounded-full text-xs w-full placeholder-gray-400" placeholder="Search Friends">
      </div>
      <div class="mt-5 space-y-6">
        <div class="flex items-center space-x-4">
          <img class="w-10 h-10 rounded-full" src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144" alt="My profile">
          <div class="flex flex-1 flex-col leading-tight">
            <div class="flex items-center justify-between">
              <span class="text-sm font-semibold text-blue-600">Lina Roy</span>
              <span class="text-xxs text-gray-400">10:34 PM</span>
            </div>
            <div class="flex items-center justify-between">
              <span class="text-xs text-gray-600">Then ok, lets meeting with client tomorrow</span>
              <span class="px-2 inline-flex items-center justify-center w-4 h-4 rounded-full bg-blue-500 text-white text-xxs">1</span>
            </div>
          </div>
        </div>
        <div class="flex items-center space-x-4">
          <img class="w-10 h-10 rounded-full" src="https://images.unsplash.com/photo-1521676129211-b7a9e7592e65?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144" alt="My profile">
          <div class="flex flex-1 flex-col leading-tight">
            <div class="flex items-center justify-between">
              <span class="text-sm font-semibold text-blue-600">Branda Frost</span>
              <span class="text-xxs text-gray-400">10:34 PM</span>
            </div>
            <div class="flex items-center justify-between">
              <span class="text-xs text-gray-600">Nice to meet you!</span>
              <span class="">
                <svg class="text-blue-400 h-4 w-4" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                </svg>
              </span>
            </div>
          </div>
        </div>
        <div class="flex items-center space-x-4">
          <img class="w-10 h-10 rounded-full" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144" alt="My profile">
          <div class="flex flex-1 flex-col leading-tight">
            <div class="flex items-center justify-between">
              <span class="text-sm font-semibold text-blue-600">Paul Irish</span>
              <span class="text-xxs text-gray-400">10:34 PM</span>
            </div>
            <div class="flex items-center justify-between">
              <span class="text-xs text-gray-600">That's Great, then star working from tomorrow</span>
              <span class="px-2 inline-flex items-center justify-center w-4 h-4 rounded-full bg-blue-500 text-white text-xxs">1</span>
            </div>
          </div>
        </div>
        <div class="flex items-center space-x-4">
          <img class="w-10 h-10 rounded-full" src="https://images.unsplash.com/photo-1544717304-a2db4a7b16ee?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144" alt="My profile">
          <div class="flex flex-1 flex-col leading-tight">
            <span class="text-sm font-semibold text-blue-600">Jessica Gilay</span>
            <span class="text-xs text-gray-600">That's sounds good</span>
          </div>
        </div>
        <div class="flex items-center space-x-4">
          <img class="w-10 h-10 rounded-full" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144" alt="My profile">
          <div class="flex flex-1 flex-col leading-tight">
            <span class="text-sm font-semibold text-blue-600">Jhon Doe</span>
            <span class="text-xs text-gray-600">Hi sir, the second comparent will be completeday today, that's ok?</span>
          </div>
        </div>
        <div class="flex items-center space-x-4">
          <img class="w-10 h-10 rounded-full" src="https://images.unsplash.com/photo-1590031905470-a1a1feacbb0b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144" alt="My profile">
          <div class="flex flex-1 flex-col leading-tight">
            <span class="text-sm font-semibold text-blue-600">Eric Peterson</span>
            <span class="text-xs text-gray-600">Firs of all meet with the compray CEO and BDA.</span>
          </div>
        </div>
      </div>
    </div>
    <div class="flex-1 p:2 sm:p-6 justify-between flex flex-col">
      <div class="flex flex-col sm:flex-row items-center justify-between py-3 border-b-2 border-gray-200">
        <div class="flex items-center space-x-4">
          <img class="w-10 sm:w-16 h-10 sm:h-16 rounded-full" src="https://images.unsplash.com/photo-1549078642-b2ba4bda0cdb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144" alt="">
          <div class="flex flex-col leading-tight">
            <div class="text-2xl mt-1 flex items-center">
              <span class="text-gray-700 mr-3">Anderson Vanhron</span>
              <span class="text-green-500">
                <svg width="10" height="10">
                  <circle cx="5" cy="5" r="5" fill="currentColor" />
                </svg>
              </span>
            </div>
            <span class="text-lg text-gray-600">Junior Developer</span>
          </div>
        </div>
        <div class="flex items-center space-x-2">
          <button type="button" class="block inline-flex items-center justify-center rounded-full h-10 w-10 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none" >
            <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
            </svg>
          </button>
          <button type="button" class="block inline-flex items-center justify-center rounded-full h-10 w-10 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none" >
            <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
            </svg>
          </button>
          <button type="button" class="block inline-flex items-center justify-center rounded-full h-10 w-10 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none" >
            <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" />
            </svg>
          </button>
        </div>
      </div>
      <div ref="messages" class="flex flex-col space-y-4 p-3 overflow-y-auto scrollbar-thumb-blue scrollbar-thumb-rounded scrollbar-track-blue-lighter scrollbar-w-2 scrolling-touch">
        <d-chat-message
          v-for="({ messages, avatar, sent }, i) of chat" :key="i"
          :avatar="avatar"
          :messages="messages"
          :sent="sent"
        />
      </div>
      <div class="border-t-2 border-gray-200 px-4 pt-4 mb-2 sm:mb-0">
        <div class="relative flex">
          <span class="absolute inset-y-0 flex items-center">
            <button type="button" class="block inline-flex items-center justify-center rounded-full h-12 w-12 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none">
              <svg class="h-6 w-6 text-gray-600" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11a7 7 0 01-7 7m0 0a7 7 0 01-7-7m7 7v4m0 0H8m4 0h4m-4-8a3 3 0 01-3-3V5a3 3 0 116 0v6a3 3 0 01-3 3z" />
              </svg>
            </button>
          </span>
          <input v-model="message" type="text" class="w-full focus:outline-none focus:placeholder-gray-400 text-gray-600 placeholder-gray-600 pl-12 bg-gray-200 rounded-full py-3" placeholder="Write Something" @keypress.enter="sent">
          <div class="absolute right-0 items-center inset-y-0 hidden sm:flex">
            <button type="button" class="block inline-flex items-center justify-center rounded-full h-10 w-10 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none">
              <svg class="h-6 w-6 text-gray-600" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.172 7l-6.586 6.586a2 2 0 102.828 2.828l6.414-6.586a4 4 0 00-5.656-5.656l-6.415 6.585a6 6 0 108.486 8.486L20.5 13" />
              </svg>
            </button>
            <button type="button" class="block inline-flex items-center justify-center rounded-full h-10 w-10 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none">
              <svg class="h-6 w-6 text-gray-600" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z" />
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z" />
              </svg>
            </button>
            <button type="button" class="block inline-flex items-center justify-center rounded-full h-10 w-10 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none">
              <svg class="h-6 w-6 text-gray-600" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.828 14.828a4 4 0 01-5.656 0M9 10h.01M15 10h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
            </button>
            <button type="button" class="block inline-flex items-center justify-center rounded-full h-12 w-12 transition duration-500 ease-in-out text-white bg-blue-500 hover:bg-blue-400 focus:outline-none" @click="sent">
              <svg class="h-6 w-6 transform rotate-90" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
                <path d="M10.894 2.553a1 1 0 00-1.788 0l-7 14a1 1 0 001.169 1.409l5-1.429A1 1 0 009 15.571V11a1 1 0 112 0v4.571a1 1 0 00.725.962l5 1.428a1 1 0 001.17-1.408l-7-14z" />
              </svg>
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="hidden sm:block w-1/5 p-3 bg-gray-200">
      <div class="relative mt-6 flex">
        <span class="absolute inset-y-0 pl-4 flex items-center">
          <svg class="h-4 w-4 text-gray-400" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
          </svg>
        </span>
        <input type="text" class="py-2 pl-10 rounded-full text-xs w-full placeholder-gray-400" placeholder="Search People">
      </div>
      <div class="flex flex-col items-center mt-6">
        <img class="w-24 h-24 rounded-full" src="https://images.unsplash.com/photo-1549078642-b2ba4bda0cdb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=3&w=144&h=144" alt="">
        <span class="text-2xl mt-1 text-gray-700">Anderson Vanhron</span>
        <span class="text-lg text-gray-600">Junior Developer</span>
      </div>
      <div class="mt-6 flex justify-between">
        <div class="flex flex-col items-center p-3">
          <span class="bg-blue-200 w-16 h-16 flex rounded-full items-center justify-center">
            <svg class="h-8 w-8 text-blue-500" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
              <path fill-rule="evenodd" d="M18 10c0 3.866-3.582 7-8 7a8.841 8.841 0 01-4.083-.98L2 17l1.338-3.123C2.493 12.767 2 11.434 2 10c0-3.866 3.582-7 8-7s8 3.134 8 7zM7 9H5v2h2V9zm8 0h-2v2h2V9zM9 9h2v2H9V9z" clip-rule="evenodd" />
            </svg>
          </span>
          <span class="text-gray-600 mt-2">Chat</span>
        </div>
        <div class="border-r-2 border-gray-300"></div>
        <div class="flex flex-col items-center p-3">
          <span class="bg-blue-200 w-16 h-16 flex rounded-full items-center justify-center">
            <svg class="h-8 w-8 text-blue-500" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
              <path d="M2 6a2 2 0 012-2h6a2 2 0 012 2v8a2 2 0 01-2 2H4a2 2 0 01-2-2V6zM14.553 7.106A1 1 0 0014 8v4a1 1 0 00.553.894l2 1A1 1 0 0018 13V7a1 1 0 00-1.447-.894l-2 1z" />
            </svg>
          </span>
          <span class="text-gray-600 mt-2">Video Call</span>
        </div>
      </div>
      <div class="flex flex-col mt-6">
        <button type="button" class="text-gray-700 flex items-center px-2 px-1 mb-3 focus:outline-none hover:text-gray-600">
          <svg class="w-6 h-6 mr-2" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
          </svg>
          <span>View Friends</span>
        </button>
        <button type="button" class="text-gray-700 flex items-center px-2 px-1 mb-3 focus:outline-none hover:text-gray-600">
          <svg class="w-6 h-6  mr-2" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
          </svg>
          <span>Add to Favorites</span>
        </button>
      </div>
      <div class="flex flex-col space-y-4 mt-3">
        <label class="text-gray-800 font-semibold text-sm" for="view-all">Attachments</label>
        <ul class="p-1 flex jusutify-between space-x-1">
          <li class="h-16 w-1/4 bg-blue-200 flex items-center justify-center text-blue-600 text-xs rounded-md">PDF</li>
          <li class="h-16 w-1/4 bg-blue-200 flex items-center justify-center text-blue-600 text-xs rounded-md">Vieo</li>
          <li class="h-16 w-1/4 bg-blue-200 flex items-center justify-center text-blue-600 text-xs rounded-md">MP3</li>
          <li class="h-16 w-1/4 bg-blue-200 flex items-center justify-center text-blue-600 text-xs rounded-md">Image</li>
        </ul>
        <div class="flex justify-center">
          <a href="#" class="text-xs px-2 border-2 rounded-full text-blue-600 border-blue-600 leading-tight hover:bg-blue-100" name="view-all">
            View All
          </a>
        </div>
      </div>
    </div>
  </div>
</template>
