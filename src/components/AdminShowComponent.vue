<template>
  <transition name="fadecard">
    <div :key="showStore.currentShow.id" v-if="showStore.currentShow.id">
      <div class="bg-gradient-to-t from-[#262626]/0 to-[#666666] pt-8 px-4 laptop:flex tablet:px-8 relative">

        <div @click.stop="openEditShow = true" v-if="userStore.isAdmin || userStore.iscoHost" class="absolute top-4 right-4 group cursor-pointer">
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path class="fill-[#CCCCCC]/80 group-hover:fill-[#CCCCCC]/60 group-active:fill-[#CCCCCC]/80" d="M15.74 3.59283C16.0867 3.24622 16.0867 2.66852 15.74 2.33968L13.6603 0.259964C13.3315 -0.0866546 12.7538 -0.0866546 12.4072 0.259964L10.7718 1.8864L14.1047 5.21928M0 12.6671V16H3.33287L13.1626 6.16137L9.82975 2.8285L0 12.6671Z" />
          </svg>
        </div>

        <div class="w-[152px] laptop:flex-none laptop:max-h-[248px] laptop:w-[248px] aspect-square laptop:mr-4 laptop:ml-0 overflow-hidden rounded-[10px] mx-auto shadow-img-shadow">
                    <img class="w-full h-full" :src="showStore.currentShow.cover_img" alt="">
                </div>
                <div class="flex-1">
                    <div class="flex justify-between items-center mt-8  laptop:mt-8">
                        <h1 class="text-white text-lg  font-semibold">{{ showStore.currentShow.title }}</h1>

                        <div class="my-4 mx-4 tablet:mx-8 flex gap-x-2 items-center justify-end">
                            <div v-if="showStore.currentShow.apple_podcast">
                                <a :href="showStore.currentShow.apple_podcast" target="_blank">
                                    <svg width="26" height="20" viewBox="0 0 26 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                                        <path class="stroke-[#FF6666]" d="M21.4853 15.6436C23.1635 14.4322 24.3064 12.8888 24.7694 11.2086C25.2324 9.52844 24.9948 7.78687 24.0865 6.20416C23.1783 4.62145 21.6402 3.26868 19.6668 2.31693C17.6934 1.36517 15.3734 0.857178 13 0.857178C10.6266 0.857178 8.30656 1.36517 6.33318 2.31693C4.35979 3.26868 2.82172 4.62145 1.91346 6.20416C1.00521 7.78687 0.767561 9.52844 1.23057 11.2086C1.69358 12.8888 2.83646 14.4322 4.51467 15.6436" stroke-width="1.33333" stroke-linecap="round" stroke-linejoin="round"/>
                                        <path class="stroke-[#FF6666]" d="M12.688 19.1429H13.312C13.9621 19.143 14.5898 18.9717 15.0772 18.6612C15.5646 18.3507 15.8781 17.9224 15.9587 17.4568L16.6253 13.6072C16.6722 13.3363 16.6388 13.0614 16.5272 12.8005C16.4156 12.5397 16.2285 12.2991 15.9782 12.0944C15.7279 11.8898 15.4201 11.726 15.0754 11.6138C14.7307 11.5016 14.3568 11.4436 13.9787 11.4437H12.0213C11.6432 11.4436 11.2693 11.5016 10.9246 11.6138C10.5799 11.726 10.2721 11.8898 10.0218 12.0944C9.77154 12.2991 9.58439 12.5397 9.47281 12.8005C9.36124 13.0614 9.32779 13.3363 9.37468 13.6072L10.0413 17.4568C10.122 17.9224 10.4354 18.3507 10.9228 18.6612C11.4102 18.9717 12.0379 19.143 12.688 19.1429ZM10.3333 6.63161C10.3333 7.1421 10.6143 7.63169 11.1144 7.99266C11.6145 8.35363 12.2928 8.55643 13 8.55643C13.7073 8.55643 14.3855 8.35363 14.8856 7.99266C15.3857 7.63169 15.6667 7.1421 15.6667 6.63161C15.6667 6.12111 15.3857 5.63153 14.8856 5.27055C14.3855 4.90958 13.7073 4.70679 13 4.70679C12.2928 4.70679 11.6145 4.90958 11.1144 5.27055C10.6143 5.63153 10.3333 6.12111 10.3333 6.63161Z"  stroke-width="1.33333" stroke-linecap="round" stroke-linejoin="round"/>
                                    </svg>
                                </a>

                            </div>

                            <div v-if="showStore.currentShow.sound_cloud">

                                <a :href="showStore.currentShow.sound_cloud" target="_blank">
                                    <svg width="32" height="14" viewBox="0 0 32 14" fill="none" xmlns="http://www.w3.org/2000/svg">
                                        <path class="fill-[#FF6666]" d="M5.57087 7.01248L5.86091 10.263L5.57087 13.6785C5.55587 13.8035 5.46085 13.8986 5.35083 13.8986C5.24082 13.8986 5.1408 13.8035 5.1408 13.6785L4.86076 10.263L5.1408 7.01248C5.1408 6.90246 5.23582 6.80244 5.35083 6.80244C5.46085 6.80244 5.55587 6.90246 5.57087 7.01248ZM6.64104 4.73212C6.50101 4.73212 6.406 4.84214 6.391 4.98216L6.14096 10.263L6.391 13.6785C6.406 13.8185 6.50101 13.9286 6.64104 13.9286C6.76606 13.9286 6.87607 13.8185 6.87607 13.6785L7.16612 10.263L6.87607 4.98216C6.87607 4.84214 6.76606 4.73212 6.64104 4.73212ZM7.91623 3.52693C7.76121 3.52693 7.65119 3.63695 7.63619 3.79197L7.41616 10.293L7.63619 13.6835C7.65119 13.8385 7.76121 13.9486 7.91623 13.9486C8.05626 13.9486 8.18128 13.8385 8.18128 13.6835L8.44632 10.293L8.18128 3.79197C8.18128 3.63695 8.05626 3.52693 7.91623 3.52693ZM0.360056 8.35769C0.290045 8.35769 0.250039 8.4127 0.235037 8.48271L0 10.263L0.235037 12.0133C0.250039 12.0833 0.290045 12.1383 0.360056 12.1383C0.430067 12.1383 0.470073 12.0833 0.485076 12.0133L0.765119 10.263L0.485076 8.48271C0.470073 8.4127 0.430067 8.35769 0.360056 8.35769ZM1.54024 7.26252C1.47023 7.26252 1.41522 7.31752 1.41522 7.38753L1.09517 10.263L1.41522 13.0684C1.41522 13.1534 1.47023 13.2084 1.54024 13.2084C1.61025 13.2084 1.66526 13.1534 1.68026 13.0834L2.04032 10.263L1.68026 7.38753C1.66526 7.31752 1.61025 7.26252 1.54024 7.26252ZM2.80544 6.69243C2.72042 6.69243 2.65041 6.76244 2.64041 6.85745L2.35037 10.263L2.64041 13.5535C2.65541 13.6385 2.72543 13.7085 2.80544 13.7085C2.89045 13.7085 2.96046 13.6385 2.96046 13.5535L3.30552 10.263L2.96046 6.85745C2.96046 6.76244 2.89045 6.69243 2.80544 6.69243ZM4.07063 6.58241C3.97562 6.58241 3.89061 6.65242 3.89061 6.76244L3.60056 10.263L3.89061 13.6535C3.89061 13.7635 3.97562 13.8335 4.07063 13.8335C4.16565 13.8335 4.25066 13.7635 4.26567 13.6535L4.58571 10.263L4.26567 6.76244C4.25066 6.65242 4.16565 6.58241 4.07063 6.58241ZM16.1425 1.03655C16.0875 0.996539 16.0025 0.966534 15.9325 0.966534C15.8225 0.966534 15.7225 1.00654 15.6524 1.06155C15.5574 1.14656 15.4974 1.27158 15.4874 1.3966V1.43661L15.3224 10.273L15.4074 11.8982L15.4924 13.4835C15.5074 13.7185 15.7024 13.9136 15.9375 13.9136C16.1725 13.9136 16.3676 13.7185 16.3676 13.4835L16.5626 10.273L16.3676 1.3966C16.3475 1.24658 16.2675 1.10656 16.1425 1.03655ZM14.8073 1.80166C14.7373 1.76166 14.6673 1.73165 14.5873 1.73165C14.5073 1.73165 14.4323 1.76166 14.3672 1.80166C14.2572 1.87168 14.1872 1.9967 14.1872 2.13672L14.1722 2.22173L14.0322 10.263C14.0322 10.263 14.0322 10.278 14.1872 13.5435V13.5585C14.1872 13.6435 14.2172 13.7235 14.2722 13.7935C14.3572 13.8885 14.4673 13.9486 14.5923 13.9486C14.7023 13.9486 14.8023 13.8935 14.8723 13.8235C14.9573 13.7535 14.9973 13.6585 14.9973 13.5435L15.0123 13.2084L15.1674 10.278L15.0023 2.13672C14.9873 1.9967 14.9173 1.87168 14.8073 1.80166ZM9.23644 2.92684C9.08142 2.92684 8.94639 3.06686 8.94639 3.23189L8.72636 10.263L8.94639 13.6235C8.9614 13.7885 9.08642 13.9136 9.23644 13.9136C9.40147 13.9136 9.52649 13.7885 9.54149 13.6235L9.79153 10.263L9.54149 3.23189C9.53149 3.06686 9.40647 2.92684 9.23644 2.92684ZM28.0744 6.06733C27.5343 6.06733 27.0192 6.17735 26.5441 6.37238C26.2241 2.83183 23.2536 0.0513916 19.6281 0.0513916C18.7379 0.0513916 17.8778 0.216417 17.1127 0.521465C16.8076 0.631482 16.7226 0.741499 16.7226 0.981537V13.4685C16.7226 13.7185 16.9176 13.8986 17.1527 13.9286H28.0694C30.2347 13.9286 32 12.1783 32 10.0129C32.005 7.8326 30.2397 6.06733 28.0744 6.06733ZM13.2371 3.05186C13.027 3.05186 12.862 3.21689 12.847 3.44192L12.682 10.278L12.847 13.5585C12.862 13.7685 13.027 13.9336 13.2371 13.9336C13.4471 13.9336 13.6121 13.7685 13.6121 13.5585L13.8072 10.278L13.6121 3.44192C13.5971 3.21689 13.4471 3.05186 13.2371 3.05186ZM10.5566 2.6618C10.3916 2.6618 10.2366 2.81682 10.2366 2.99685L10.0416 10.263L10.2366 13.6085C10.2516 13.7885 10.3916 13.9286 10.5566 13.9286C10.7367 13.9286 10.8767 13.7885 10.8917 13.6085L11.1117 10.263L10.8917 2.99685C10.8767 2.81682 10.7367 2.6618 10.5566 2.6618ZM11.8919 2.83183C11.6968 2.83183 11.5468 2.98685 11.5468 3.17688L11.3518 10.263L11.5468 13.5835C11.5618 13.7785 11.7018 13.9286 11.8919 13.9286C12.0819 13.9286 12.2369 13.7735 12.2369 13.5835L12.4469 10.263L12.2369 3.17688C12.2369 2.98185 12.0869 2.83183 11.8919 2.83183Z" />
                                    </svg>                            
                                </a>

                            </div>

                            <div v-if="showStore.currentShow.pod_beam">
                                <a :href="showStore.currentShow.pod_beam">
                                    <svg width="25" height="24" viewBox="0 0 25 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                        <path class="fill-[#FF6666]" d="M4.1978 0.193478C2.97464 0.503574 2.3889 0.848127 1.54474 1.76119C0.631678 2.74317 0.407719 3.29446 0.149304 5.03445C-0.126339 6.87781 0.0114823 18.9889 0.304353 20.1603C0.700589 21.6419 2.31999 23.313 3.8188 23.7609C4.85246 24.071 19.7372 24.0882 20.7708 23.7609C22.6831 23.1924 24.0613 21.573 24.4231 19.5229C24.6987 17.938 24.6643 5.6891 24.3886 4.32812C23.9924 2.41585 23.0621 1.26159 21.236 0.434664C20.409 0.0384274 20.3057 0.0384274 12.7255 0.00397301C7.02314 -0.0132561 4.83523 0.0212002 4.1978 0.193478ZM15.0168 5.91306C17.0324 6.42989 19.0997 7.75642 20.3401 9.30691C21.3221 10.5645 21.2015 11.4948 20.03 11.4948C19.5649 11.4948 19.3754 11.357 18.893 10.7024C18.1694 9.68592 16.6189 8.51444 15.3441 8.04929C13.8453 7.46355 11.554 7.39464 10.0208 7.84256C8.48749 8.32494 6.97146 9.30691 5.9378 10.5128C4.97305 11.6499 4.33563 11.8222 3.83602 11.0641C3.43979 10.4612 3.64652 10.0649 5.04196 8.66949C6.35126 7.34296 8.00512 6.34375 9.64174 5.91306C10.8994 5.56851 13.7075 5.56851 15.0168 5.91306ZM15.1891 9.90988C16.395 10.5128 17.8938 11.96 17.8938 12.5457C17.8938 12.9936 17.2908 13.5621 16.8429 13.5621C16.6189 13.5621 16.1366 13.2176 15.6714 12.7352C13.7075 10.6851 11.175 10.6507 9.15937 12.6146C8.16017 13.6138 7.71225 13.7516 7.17819 13.2693C6.73027 12.873 6.79918 12.3045 7.33324 11.6326C8.74591 9.94434 10.3825 9.22077 12.6738 9.30691C13.8281 9.3586 14.2588 9.46196 15.1891 9.90988ZM14.2243 13.7689C16.1538 15.0437 15.9643 18.0413 13.897 19.0922C12.8633 19.6263 11.2956 19.5057 10.3998 18.8338C9.21105 17.9207 8.81482 16.3703 9.43501 15.0265C10.0208 13.7516 10.9855 13.1831 12.4843 13.2693C13.2768 13.3037 13.7247 13.4243 14.2243 13.7689Z"/>
                                    </svg>                            
                                </a>
                            </div>

                            <div v-if="showStore.currentShow.spotify">
                                <a :href="showStore.currentShow.spotify" target="_blank">
                                    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                        <path class="fill-[#FF6666]" d="M12 0C5.37581 0 0 5.37581 0 12C0 18.6242 5.37581 24 12 24C18.6242 24 24 18.6242 24 12C24 5.37581 18.6242 0 12 0ZM16.8726 17.6565C16.6694 17.6565 16.5435 17.5935 16.3548 17.4823C13.3355 15.6629 9.82258 15.5855 6.35323 16.2968C6.16452 16.3452 5.91774 16.4226 5.77742 16.4226C5.30806 16.4226 5.0129 16.05 5.0129 15.6581C5.0129 15.1597 5.30806 14.9226 5.67097 14.8452C9.63387 13.9694 13.6839 14.0468 17.1387 16.1129C17.4339 16.3016 17.6081 16.471 17.6081 16.9113C17.6081 17.3516 17.2645 17.6565 16.8726 17.6565ZM18.1742 14.4823C17.9226 14.4823 17.7532 14.371 17.579 14.279C14.5548 12.4887 10.0452 11.7677 6.03387 12.8565C5.80161 12.9194 5.67581 12.9823 5.45806 12.9823C4.94032 12.9823 4.51935 12.5613 4.51935 12.0435C4.51935 11.5258 4.77097 11.1823 5.26935 11.0419C6.61452 10.6645 7.98871 10.3839 10.0016 10.3839C13.1419 10.3839 16.1758 11.1629 18.5661 12.5855C18.9581 12.8177 19.1129 13.1177 19.1129 13.5387C19.1081 14.0613 18.7016 14.4823 18.1742 14.4823ZM19.6742 10.7952C19.4226 10.7952 19.2677 10.7323 19.05 10.6065C15.6048 8.55 9.44516 8.05645 5.45806 9.16935C5.28387 9.21774 5.06613 9.29516 4.83387 9.29516C4.19516 9.29516 3.70645 8.79677 3.70645 8.15323C3.70645 7.49516 4.1129 7.12258 4.54839 6.99677C6.25161 6.49839 8.15806 6.26129 10.2339 6.26129C13.7661 6.26129 17.4677 6.99677 20.1726 8.57419C20.55 8.79193 20.7968 9.09194 20.7968 9.66774C20.7968 10.3258 20.2645 10.7952 19.6742 10.7952Z" />
                                    </svg>
                                </a>
                            </div>

                            <div v-if="showStore.currentShow.google_podcast">
                                <a :href="showStore.currentShow.google_podcast">
                                    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                        <path class="fill-[#FF6666]" d="M18.816 6.264V7.944C18.816 8.76 18.156 9.432 17.316 9.432C16.488 9.432 15.816 8.76 15.816 7.944V6.264C15.816 5.86618 15.974 5.48464 16.2553 5.20334C16.5366 4.92204 16.9182 4.764 17.316 4.764C18.156 4.764 18.816 5.436 18.816 6.264ZM13.5 7.632V16.356C13.5 16.7538 13.342 17.1354 13.0607 17.4167C12.7794 17.698 12.3978 17.856 12 17.856C11.6022 17.856 11.2206 17.698 10.9393 17.4167C10.658 17.1354 10.5 16.7538 10.5 16.356V7.632C10.5 6.816 11.172 6.132 12 6.132C12.828 6.132 13.5 6.816 13.5 7.632ZM24 11.16V12.84C24 13.656 23.328 14.328 22.5 14.328C21.672 14.328 21 13.656 21 12.84V11.16C21 10.332 21.672 9.672 22.5 9.672C23.328 9.672 24 10.332 24 11.16ZM3 11.16V12.84C3 13.656 2.328 14.328 1.5 14.328C0.66 14.328 0 13.656 0 12.84V11.16C0 10.332 0.66 9.672 1.5 9.672C2.328 9.672 3 10.332 3 11.16ZM8.184 16.056V17.724C8.184 18.54 7.512 19.2 6.684 19.2C5.856 19.2 5.184 18.54 5.184 17.724V16.056C5.184 15.216 5.856 14.556 6.684 14.556C7.08183 14.556 7.46336 14.714 7.74466 14.9953C8.02596 15.2766 8.184 15.6582 8.184 16.056ZM13.5 20.832V22.5C13.5 22.8978 13.342 23.2794 13.0607 23.5607C12.7794 23.842 12.3978 24 12 24C11.6022 24 11.2206 23.842 10.9393 23.5607C10.658 23.2794 10.5 22.8978 10.5 22.5V20.832C10.5 20.4342 10.658 20.0526 10.9393 19.7713C11.2206 19.49 11.6022 19.332 12 19.332C12.3978 19.332 12.7794 19.49 13.0607 19.7713C13.342 20.0526 13.5 20.4342 13.5 20.832ZM13.5 1.5V3.168C13.5 3.56582 13.342 3.94736 13.0607 4.22866C12.7794 4.50996 12.3978 4.668 12 4.668C11.6022 4.668 11.2206 4.50996 10.9393 4.22866C10.658 3.94736 10.5 3.56582 10.5 3.168V1.5C10.5 0.66 11.172 0 12 0C12.3978 0 12.7794 0.158035 13.0607 0.43934C13.342 0.720644 13.5 1.10218 13.5 1.5ZM18.816 12.408V17.724C18.816 18.552 18.156 19.2 17.316 19.2C16.488 19.2 15.816 18.552 15.816 17.724V12.408C15.816 11.568 16.488 10.908 17.316 10.908C18.156 10.908 18.816 11.568 18.816 12.408ZM8.184 6.264V11.58C8.184 12.42 7.512 13.08 6.684 13.08C6.48702 13.08 6.29196 13.0412 6.10998 12.9658C5.92799 12.8904 5.76263 12.7799 5.62334 12.6407C5.48405 12.5014 5.37356 12.336 5.29818 12.154C5.2228 11.972 5.184 11.777 5.184 11.58V6.264C5.184 5.86618 5.34204 5.48464 5.62334 5.20334C5.90464 4.92204 6.28618 4.764 6.684 4.764C7.08183 4.764 7.46336 4.92204 7.74466 5.20334C8.02596 5.48464 8.184 5.86618 8.184 6.264Z" />
                                    </svg>                            
                                </a>

                            </div>
                        </div>
                    </div>


                    <div class="flex justify-between">
                        <div class="flex gap-x-1 items-center">
                            <div>
                                <svg width="8" height="8" viewBox="0 0 8 8" fill="none" xmlns="http://www.w3.org/2000/svg">
                                    <circle cx="4" cy="4" r="4" class="fill-[#E84344]" fill-opacity="0.4"/>
                                </svg>
                            </div>
                            <span class="text-white/80 text-sm font-medium">{{ showStore.seasonCount }} seasons</span>
                        </div>

                        <div>
                            <span class="text-white/80 text-sm font-medium">{{ total_likes }} likes</span>
                        </div>
                    </div>

                    <p :class="[drop ? 'line-clamp-none' : 'line-clamp-4']" class="text-white/80  text-base leading-7 laptop:min-h-[96px]">{{ showStore.currentShow.description }}</p>
                    <span @click.stop="dropdesc" class="text-white/80 font-semibold text-x-sm">{{ drop ? 'less...' : 'more...' }}</span>

                </div>

      </div>

        <div class="text-end mx-4 mt-4 tablet:mx-8" v-if="userStore.isAdmin || userStore.iscoHost">
          <button class="
                text-base 
                text-white 
                font-medium
                bg-[#D9D9D9]/10  
                rounded-[15px]
                px-3 py-1
                transition
                hover:bg-[#D9D9D9]/5
                active:bg-[#D9D9D9]/10" @click="opneAddEpisode = true">New episode</button>
        </div>

        
        <EpisodeListComponent @editEpisode="editEpisode"/>

      </div>
  </transition>



    <Teleport to="body">

        <transition name="modal">
        
            <div v-if="openEditShow" class="modal-mask">
                <div class="modal-container rounded-[10px] relative">
                    <button @click="openEditShow = false; editEpi = {}" class="absolute left-1 top-1 group" type="button">
                      <div class="w-8 h-8">
                        <svg class="w-full h-full" viewBox="0 0 17 18" fill="none" xmlns="http://www.w3.org/2000/svg">
                          <path d="M6.2376 11.2624L8.5008 9ZM10.7632 6.7376L8.5008 9ZM8.5008 9L6.2376 6.7376ZM8.5008 9L10.7632 11.2624ZM8.5 17C12.9184 17 16.5 13.4184 16.5 9C16.5 4.5816 12.9184 1 8.5 1C4.0816 1 0.5 4.5816 0.5 9C0.5 13.4184 4.0816 17 8.5 17Z" class="fill-white/80 group-hover:fill-white/40 group-active:fill-white/60"/>
                          <path d="M6.2376 11.2624L8.5008 9M8.5008 9L10.7632 6.7376M8.5008 9L6.2376 6.7376M8.5008 9L10.7632 11.2624M8.5 17C12.9184 17 16.5 13.4184 16.5 9C16.5 4.5816 12.9184 1 8.5 1C4.0816 1 0.5 4.5816 0.5 9C0.5 13.4184 4.0816 17 8.5 17Z" class="stroke-black/40" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                      </div>
                    </button>

                    <div class="flex overflow-hidden">

                      <div class="w-full" ref="addShow">
                        <AddShowComponent @scrollToAddUser="scrollToAddUser" :currentShow="{...showStore.currentShow, 'isEdit' : true}" @close="close"/>
                      </div>

                      <!-- <div class="w-[240px] flex-none" ref="addUser"> -->
                        <!-- <AdduserCOmponent @scrollToAddShow="scrollToAddShow"/> -->
                      <!-- </div> -->

                    </div>


                </div>

            </div>                
        </transition>

    </Teleport>

    <Teleport to="body">
        <transition name="modal">
        
            <div v-if="opneAddEpisode" class="modal-mask">
                <div class="modal-container laptop:w-[50%] rounded-[10px] relative">
                    <button @click="opneAddEpisode = false; editEpi = {}; scrollToAddShow()" class="absolute left-1 top-1 group" type="button">
                      <div class="w-8 h-8">
                        <svg class="w-full h-full" viewBox="0 0 17 18" fill="none" xmlns="http://www.w3.org/2000/svg">
                          <path d="M6.2376 11.2624L8.5008 9ZM10.7632 6.7376L8.5008 9ZM8.5008 9L6.2376 6.7376ZM8.5008 9L10.7632 11.2624ZM8.5 17C12.9184 17 16.5 13.4184 16.5 9C16.5 4.5816 12.9184 1 8.5 1C4.0816 1 0.5 4.5816 0.5 9C0.5 13.4184 4.0816 17 8.5 17Z" class="fill-white/80 group-hover:fill-white/40 group-active:fill-white/60"/>
                          <path d="M6.2376 11.2624L8.5008 9M8.5008 9L10.7632 6.7376M8.5008 9L6.2376 6.7376M8.5008 9L10.7632 11.2624M8.5 17C12.9184 17 16.5 13.4184 16.5 9C16.5 4.5816 12.9184 1 8.5 1C4.0816 1 0.5 4.5816 0.5 9C0.5 13.4184 4.0816 17 8.5 17Z" class="stroke-black/40" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                      </div>
                    </button>

                    <div class="flex overflow-x-hidden">

                      <div class="flex-none w-full" ref="addEpisode">
                        <AddEpisodeComponent :editEpi="editEpi" :seasons="showStore.currentShow.seasons" @close="opneAddEpisode = false" @scrollToAddUser="scrollToAddUser"/>
                      </div>

                      <div class="flex-none w-full flex items-center" ref="addUser">
                        <AddUserComponent @scrollToAddShow="scrollToAddShow"/>
                      </div>

                    </div>


                </div>

            </div>                
        </transition>

    </Teleport>
</template>

<script setup>
import { computed, onBeforeMount, ref } from 'vue';
import { useShowsStore } from '../stores/ShowsStore';
import {useRoute} from 'vue-router';
import AddShowComponent from '../components/AddShowComponent.vue';
import EpisodeListComponent from './EpisodeListComponent.vue';
import AddEpisodeComponent from '../components/AddEpisodeComponent.vue';
import AddUserComponent from '../components/AdduserComponent.vue';
import { useUserStore } from '../stores/userStore';

const userStore = useUserStore();
const showStore = useShowsStore();
const route = useRoute();
const openEditShow = ref(false);
const opneAddEpisode = ref(false);
const addUser = ref(null);
const addEpisode = ref(null);
const drop = ref(false);
const editEpi = ref({});

onBeforeMount(async () => {
    if (!userStore.users.length) {
        userStore.getUsers();
    }
    await showStore.getShow(route.params.id);
})

function dropdesc () {
    drop.value = !drop.value;
}

function scrollToAddUser() {
  addUser.value.scrollIntoView({behavior : 'smooth', inline : 'end'});
}

function scrollToAddShow() {
  addEpisode.value.scrollIntoView({behavior : 'smooth', inline : 'start'});
}


function close() {
    openEditShow.value = false;
    editEpi.value = {};
}

function editEpisode(epi) {
  console.log(epi);
  opneAddEpisode.value = true;
  editEpi.value = epi;
}


const total_likes = computed(() => {
    let totallikes = 0;
    if (Object.keys(showStore.currentShow).length) {
        for(let i = 0; i < showStore.currentShow.seasons.length; i++) {

            for (let j = 0; j < showStore.currentShow.seasons[i].episodes.length; j++) {
                totallikes += showStore.currentShow.seasons[i].episodes[j].number_of_likes;
            }
            }

            return totallikes;
    }

    return 0;

})

</script>

<style>

.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  transition: opacity 0.3s ease;
}

.modal-container {
  margin: auto;
  padding: 20px 30px;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;

}

.modal-enter-from {
  opacity: 0;
}

.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}

.fadecard-enter-active,
.fadecard-leave-active {
  transition: opacity 0.3s ease;
}

.fadecard-enter-from,
.fadecard-leave-to {
  opacity: 0;
}

.fadecard-leave-active {
    position: absolute;
}

</style>