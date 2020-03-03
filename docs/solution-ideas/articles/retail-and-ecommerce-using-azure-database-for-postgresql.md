---
title: Retail and e-commerce using Azure PostgreSQL
titleSuffix: Azure Solution Ideas
author: adamboeglin
ms.date: 12/16/2019
description: Build secure and scalable e-commerce solutions that meet the demands of both customers and business. Engage customers through customized products and offers, process transactions quickly and securely, and focus on fulfillment and customer service.
ms.custom: acom-architecture, web-app, ecommerce, postgresql, use cases, azure, solutions, 'https://azure.microsoft.com/solutions/architecture/retail-and-ecommerce-using-azure-database-for-postgresql/'
ms.service: architecture-center
ms.subservice: solution-idea
---
# Retail and e-commerce using Azure Database for PostgreSQL

[!INCLUDE [header_file](../header.md)]

Build secure and scalable e-commerce solutions that meet the demands of both customers and business. Engage customers through customized products and offers, process transactions quickly and securely, and focus on fulfillment and customer service. 

## Architecture

<svg class="architecture-diagram" aria-labelledby="retail-and-ecommerce-using-azure-database-for-postgresql" height="285.39" viewbox="0 0 595.565 285.39"  xmlns="http://www.w3.org/2000/svg">
    <text fill="#5b5b5b" font-family="SegoeUI, Segoe UI" font-size="14" transform="translate(3.797 91.785)">
        B<tspan letter-spacing="-.013em" x="8.025" y="0">r</tspan><tspan x="12.708" y="0">owser</tspan>
    </text>
    <path d="M0 61.653A2.354 2.354 0 002.347 64h53.991a2.354 2.354 0 002.347-2.347V24.915H0z" fill="#59b4d9"/>
    <path d="M56.338 14H2.347A2.354 2.354 0 000 16.347v8.92h58.685v-8.92A2.354 2.354 0 0056.338 14" fill="#a0a1a2"/>
    <path d="M2.347 14A2.354 2.354 0 000 16.347v45.306A2.354 2.354 0 002.347 64H4.93l46.244-50z" fill="#fff" opacity=".2" style="isolation:isolate"/>
    <path fill="#fff" d="M17.305 17.181h38.371v4.514H17.305z"/>
    <circle cx="7.9" cy="19.814" fill="#3999c6" r="2.633"/>
    <text fill="#5b5b5b" font-family="SegoeUI, Segoe UI" font-size="14" transform="translate(321.778 87.285)">
        Azu<tspan letter-spacing="-.013em" x="23.283" y="0">r</tspan><tspan x="27.966" y="0">e Data</tspan><tspan letter-spacing="-.013em" x="67.929" y="0">b</tspan><tspan x="75.975" y="0">ase </tspan><tspan x="3.989" y="16.8">for </tspan><tspan letter-spacing="-.037em" x="25.276" y="16.8">P</tspan><tspan x="32.597" y="16.8">os</tspan><tspan letter-spacing="-.008em" x="46.741" y="16.8">t</tspan><tspan x="51.375" y="16.8">g</tspan><tspan letter-spacing="-.013em" x="59.62" y="16.8">r</tspan><tspan x="64.302" y="16.8">eSQL</tspan><tspan x="-3.845" y="33.6">(P</tspan><tspan letter-spacing="-.013em" x="8.22" y="33.6">r</tspan><tspan x="12.903" y="33.6">oduct Catalog)</tspan>
    </text>
    <text fill="#5b5b5b" font-family="SegoeUI, Segoe UI" font-size="14" transform="translate(321.778 247.285)">
        Azu<tspan letter-spacing="-.013em" x="23.283" y="0">r</tspan><tspan x="27.966" y="0">e Data</tspan><tspan letter-spacing="-.013em" x="67.929" y="0">b</tspan><tspan x="75.975" y="0">ase </tspan><tspan x="3.989" y="16.8">for </tspan><tspan letter-spacing="-.037em" x="25.276" y="16.8">P</tspan><tspan x="32.597" y="16.8">os</tspan><tspan letter-spacing="-.008em" x="46.741" y="16.8">t</tspan><tspan x="51.375" y="16.8">g</tspan><tspan letter-spacing="-.013em" x="59.62" y="16.8">r</tspan><tspan x="64.302" y="16.8">eSQL</tspan><tspan x="5.472" y="33.6">(Session </tspan><tspan letter-spacing="-.032em" x="59.688" y="33.6">S</tspan><tspan x="66.674" y="33.6">ta</tspan><tspan letter-spacing="-.008em" x="78.542" y="33.6">t</tspan><tspan x="83.176" y="33.6">e)</tspan>
    </text>
    <text fill="#5b5b5b" font-family="SegoeUI, Segoe UI" font-size="14" transform="translate(142.145 90.785)">
        Azu<tspan letter-spacing="-.013em" x="23.283" y="0">r</tspan><tspan x="27.966" y="0">e App Se</tspan><tspan letter-spacing=".04em" x="83.207" y="0">r</tspan><tspan x="88.635" y="0">vices</tspan>
    </text>
    <text fill="#5b5b5b" font-family="SegoeUI, Segoe UI" font-size="14" transform="translate(505.337 86.785)">
        Azu<tspan letter-spacing="-.013em" x="23.283" y="0">r</tspan><tspan x="27.966" y="0">e Sea</tspan><tspan letter-spacing="-.013em" x="61.004" y="0">r</tspan><tspan x="65.687" y="0">ch</tspan><tspan x="-7.889" y="16.8">(Full-</tspan><tspan letter-spacing="-.008em" x="23.475" y="16.8">t</tspan><tspan x="28.109" y="16.8">ext index)</tspan>
    </text>
    <text fill="#5b5b5b" font-family="SegoeUI, Segoe UI" font-size="14" transform="translate(138.088 251.785)">
        Azu<tspan letter-spacing="-.013em" x="23.283" y="0">r</tspan><tspan x="27.966" y="0">e </tspan><tspan letter-spacing="-.032em" x="39.122" y="0">S</tspan><tspan letter-spacing="-.008em" x="46.108" y="0">t</tspan><tspan x="50.743" y="0">orage (Logs,</tspan><tspan x="-5.12" y="16.8">static catalog con</tspan><tspan letter-spacing="-.008em" x="102.847" y="16.8">t</tspan><tspan x="107.481" y="16.8">ent)</tspan>
    </text>
    <path fill="none" stroke="#969696" stroke-miterlimit="10" stroke-width="1.5" d="M319.54 40.03h-77.265"/>
    <path fill="#969696" d="M318.008 34.794l9.067 5.236-9.067 5.236V34.794z"/>
    <path fill="none" stroke="#969696" stroke-miterlimit="10" stroke-width="1.5" d="M153.54 40.03H72.275"/>
    <path fill="#969696" d="M152.008 34.794l9.067 5.236-9.067 5.236V34.794z"/>
    <path d="M196.051 61.22h-17.928V43.4h3.672a9.513 9.513 0 01-.648-3.564v-.216h-6.8V65h25.488V49.88h-3.78zM221.323 43.4h3.24v17.928h-17.928v-11.34h-3.78V65h25.488V39.62h-7.992a7.609 7.609 0 01.972 3.564zM178.123 32.6V14.78h17.928v10.368a10.021 10.021 0 013.78-1.728V11h-25.488v25.38h7.344a10.249 10.249 0 012.376-3.672l-5.94-.108zM206.635 22.988V14.78h17.928v17.928h-7.884a13.1 13.1 0 01.54 3.672v.108h11.124V11h-25.488v11.772c.324 0 .54-.108.864-.108a26.751 26.751 0 012.916.324z" fill="#a0a1a2"/>
    <path d="M218.407 43.076a3.987 3.987 0 00-4-4h-.54a11.741 11.741 0 00.432-2.808 10.628 10.628 0 00-20.736-3.348 8.425 8.425 0 00-2.376-.432 7.345 7.345 0 000 14.688h23.544a4.107 4.107 0 003.672-4.1" fill="#59b4d9"/>
    <path d="M195.079 47.18a7.341 7.341 0 013.564-12.312 5.967 5.967 0 012.376-.108 10.713 10.713 0 015.94-8.64 10.181 10.181 0 00-3.24-.54 10.57 10.57 0 00-10.044 7.344 8.425 8.425 0 00-2.376-.432 7.345 7.345 0 000 14.688h3.78z" fill="#fff" opacity=".2" style="isolation:isolate"/>
    <path d="M169.343 228.5a2.131 2.131 0 002.2 2.2h53.592a2.131 2.131 0 002.2-2.2v-38.4h-58z" fill="#a0a1a2"/>
    <path d="M225.139 181.292h-53.592a2.131 2.131 0 00-2.2 2.2v6.612h58V183.5a2.131 2.131 0 00-2.2-2.2" fill="#7a7a7a"/>
    <path fill="#fff" d="M191.151 193.936h14.616v8.816h-14.616z"/>
    <path fill="#fcd116" d="M191.151 205.884h14.616v8.816h-14.616zM208.551 205.884h14.616v8.816h-14.616z"/>
    <path fill="#fff" d="M208.551 193.936h14.616v8.816h-14.616zM173.751 193.936h14.616v8.816h-14.616zM173.751 205.884h14.616v8.816h-14.616z"/>
    <path fill="#fcd116" d="M173.751 217.716h14.616v8.816h-14.616zM191.151 217.716h14.616v8.816h-14.616zM208.551 217.716h14.616v8.816h-14.616z"/>
    <path d="M171.547 181.292a2.37 2.37 0 00-2.2 2.2V228.5a2.37 2.37 0 002.2 2.2h2.436l45.936-49.416z" fill="#fff" opacity=".2" style="isolation:isolate"/>
    <path d="M565.623 22.9c0-.448.112-1.008.112-1.456a14.413 14.413 0 00-14.56-14.336 14.135 14.135 0 00-11.76 5.824 10.426 10.426 0 00-5.824-1.68 10.971 10.971 0 00-10.976 10.868v.9c-4.032 2.128-6.272 5.6-6.272 9.856 0 6.72 5.488 11.984 12.544 11.984H559.8c7.056 0 12.544-5.264 12.544-11.984a10.625 10.625 0 00-6.721-9.976z" fill="#59b4d9"/>
    <path d="M524.183 38.36c0-4.592 2.352-8.176 6.72-10.416v-.9a11.754 11.754 0 0117.808-9.856 15.487 15.487 0 0112.544-6.384A15.172 15.172 0 00551.175 7a14.535 14.535 0 00-11.76 5.936 10.426 10.426 0 00-5.824-1.68 10.971 10.971 0 00-10.976 10.864v.9c-4.032 2.128-6.272 5.6-6.272 9.856a11.877 11.877 0 009.408 11.648 12.584 12.584 0 01-1.568-6.164z" fill="#fff" opacity=".2" style="isolation:isolate"/>
    <path d="M554.759 41.72a9.692 9.692 0 01-9.408 7.392 8.526 8.526 0 01-2.351-.336 10.058 10.058 0 01-3.136-1.456 10.293 10.293 0 01-2.464-2.464 9.8 9.8 0 01-1.456-7.728 9.692 9.692 0 019.408-7.392 8.526 8.526 0 012.352.336 9.758 9.758 0 015.936 4.368 9.232 9.232 0 011.12 7.28" fill="#fff"/>
    <path d="M554.759 41.72a9.692 9.692 0 01-9.408 7.392 8.526 8.526 0 01-2.351-.336 10.058 10.058 0 01-3.136-1.456 10.293 10.293 0 01-2.464-2.464 9.8 9.8 0 01-1.456-7.728 9.692 9.692 0 019.408-7.392 8.526 8.526 0 012.352.336 9.758 9.758 0 015.936 4.368 9.232 9.232 0 011.12 7.28" fill="#59b4d9" opacity=".1" style="isolation:isolate"/>
    <path d="M550.615 31.3a9.5 9.5 0 00-2.912-1.232 8.526 8.526 0 00-2.352-.336 9.692 9.692 0 00-9.408 7.392 9.3 9.3 0 001.456 7.728 7.847 7.847 0 00.9 1.12A25.051 25.051 0 01550.615 31.3" fill="#59b4d9" opacity=".3" style="isolation:isolate"/>
    <path d="M557.223 32.312a13.834 13.834 0 00-8.512-6.272 17.291 17.291 0 00-3.36-.448 13.892 13.892 0 00-13.44 10.528 13.553 13.553 0 001.456 10.192l-10.528 10.64a3.654 3.654 0 000 5.04 3.8 3.8 0 005.152 0l10.528-10.64a14.179 14.179 0 003.584 1.456 17.291 17.291 0 003.36.448A13.892 13.892 0 00558.9 42.728a14.127 14.127 0 00-1.677-10.416zm-2.464 9.408a9.692 9.692 0 01-9.408 7.392 8.526 8.526 0 01-2.351-.336 10.058 10.058 0 01-3.136-1.456 10.293 10.293 0 01-2.464-2.464 9.8 9.8 0 01-1.456-7.728 9.692 9.692 0 019.408-7.392 8.526 8.526 0 012.352.336 9.758 9.758 0 015.936 4.368 9.3 9.3 0 011.119 7.28z" fill="#3e3e3e"/>
    <path d="M537.511 50.792a13.635 13.635 0 01-3.584-3.584c-.224-.336-.336-.56-.56-.9l-.9 1.008-.112.112a2.343 2.343 0 00.448.672 16.758 16.758 0 003.92 4.032 2.676 2.676 0 00.784.336l1.008-1.008c-.444-.332-.668-.444-1.004-.668z" fill="#1e1e1e" opacity=".5" style="isolation:isolate"/>
    <path fill="#fcd116" d="M534.788 181.474l-4.625.793-4.097 1.85-3.568 2.247-3.436 4.097-1.85 1.982-1.851.661-.528-1.189.925-1.19.132-1.718h.661l.528.529-.132-1.718-.66-.529v-.661l-1.586.925-1.586 1.718-.264 1.586.66 1.322.529 2.114 1.189.529h1.322l1.189-.793-.793 4.097.793 4.493-.925 2.114-2.775 3.04.396 1.982 1.454 2.115 2.511 1.718 1.454.264h1.453l-.925 3.965 3.436 1.453 4.361.529 1.454-1.057.132-2.511 1.718-2.775.132-2.247 3.965.397 3.7-.397-3.7 2.247.661 2.643 2.246 3.7 2.379.925 1.718-.661.793-1.585 3.833-2.908.793.661 5.947.264 1.189-1.057.132-1.718-.396-.661-.265-4.625-1.982-3.965.264-1.85 1.19.661 3.436 3.171 1.586.133 1.85-.793 1.85-1.322.925-3.039 5.286.396 3.304-1.321 2.643-2.379 1.85-3.568.529-4.229-.397-4.758-1.057-4.361-1.057-1.454-1.454-.396-2.511 2.775-2.246.793-1.983-3.304-1.982-1.85-1.189-.661-4.229-3.7-3.568-1.85-3.436-.265-4.097.661-3.568 1.322-2.379 1.982-1.983 2.379-1.982.528-3.436 3.304z"/>
    <path fill="#1e1e1e" d="M516.947 197.461l.529.661.132-.793h-.396l-.265.132z"/>
    <path d="M577.738 185.307a14.653 14.653 0 00-1.586-5.286c-.132-.132-.264-.4-.4-.529a5.457 5.457 0 00-1.454-.925 1.96 1.96 0 00-1.718 0c-.132.132-.264.132-.4.264a7.33 7.33 0 00-.793 1.057 9.318 9.318 0 01-.925 1.189 5.128 5.128 0 01-1.454.793 5.128 5.128 0 00-.793-1.454 12.4 12.4 0 00-1.189-1.586l-1.057-1.057-1.189-.793a29.418 29.418 0 01-3.172-2.511c-.4-.4-.925-.793-1.322-1.189a11.711 11.711 0 00-7-3.04 19.132 19.132 0 00-7.929 1.718 13.93 13.93 0 00-3.436 2.114 18.967 18.967 0 00-2.511 2.907 3.91 3.91 0 00-1.322.264 4.69 4.69 0 00-1.586 1.057 8.55 8.55 0 01-1.189 1.057l-1.057 1.057a28.952 28.952 0 00-6.872 1.718 19.8 19.8 0 00-5.683 3.436 9.936 9.936 0 00-1.982 2.114 21.524 21.524 0 00-1.454 2.247l-1.189 1.189a2.742 2.742 0 01-1.322.793 1.023 1.023 0 01-.4.132v-.132a3.389 3.389 0 00.793-2.511c.132.132.132.264.264.4s.132.264.264.4l.264-.264.4.132a5.542 5.542 0 00.132-2.114 1.816 1.816 0 00-.661-1.057c0-.132.132-.132.132-.264a1.91 1.91 0 00.264-.925l-.264-.132.264.132.4-.264-.529.132a8.585 8.585 0 00-3.568 2.247 5.868 5.868 0 00-1.057 1.454 2.949 2.949 0 00-.4 1.718 3.97 3.97 0 00.793 1.454 8.422 8.422 0 00.264.925 1.878 1.878 0 01.264.793 2.746 2.746 0 001.454 1.322 3.221 3.221 0 001.586 0c-.132.661-.132 1.322-.264 1.982a27.663 27.663 0 00.132 3.172 1.676 1.676 0 00.132.793c0 .264.132.529.132.793a1.878 1.878 0 00-.264.793 5.523 5.523 0 01-.529 1.322l-1.057 1.057-.925.925-.264.264a1.625 1.625 0 00-.661 1.85 18.821 18.821 0 00.661 2.114 8.032 8.032 0 001.322 1.85 14.113 14.113 0 003.3 2.114 3.92 3.92 0 002.114.264c0 .132 0 .264-.132.264a6.443 6.443 0 00-.4.925c-.793 1.85 0 2.775 1.322 3.3a12.99 12.99 0 002.114.661c.132 0 .264.132.529.132a19.751 19.751 0 003.7.793c1.454.132 2.775-.264 3.172-1.586a5.816 5.816 0 00.264-1.322v-1.189a7.076 7.076 0 01.925-1.586c0-.132.132-.132.132-.264.264-.529.529-.793.529-1.189v-1.586a15.994 15.994 0 002.511.132h1.322c-.132 0-.264.132-.4.132a.129.129 0 00-.132.132c-1.189.529-1.189 1.718-.793 2.775a6.285 6.285 0 001.454 2.643 10.365 10.365 0 002.643 3.04c1.057.661 2.247.661 3.832-.132a2.746 2.746 0 001.322-1.454c.132-.132.264-.4.4-.529a19.778 19.778 0 011.982-1.586 5.6 5.6 0 01.925-.661 4.4 4.4 0 00.793.4 4.955 4.955 0 001.454.132h3.436a3.823 3.823 0 002.247-.4 2.286 2.286 0 001.057-1.982v-1.057a1.757 1.757 0 00-.4-.925v-2.907a6.633 6.633 0 00-.264-1.586 6.442 6.442 0 00-.529-1.454c-.132-.4-.264-.661-.4-1.057l-.264.132.264-.132a8.084 8.084 0 00-.661-1.586v-.4l.529.529.793.793a9.1 9.1 0 001.718 1.454 3.19 3.19 0 002.247.529 5.239 5.239 0 002.907-1.057 6.459 6.459 0 001.85-2.379c.132-.264.132-.529.264-.793 0-.264.132-.4.132-.661a15.132 15.132 0 004.229.132 11.72 11.72 0 003.832-1.057 9.717 9.717 0 003.832-3.832 14.938 14.938 0 001.85-5.947c-.112-1.584-.244-3.963-.641-6.209zM557.915 201.3c-.4 1.322-1.057 3.568.793 3.965a2.354 2.354 0 001.982-.4 3.724 3.724 0 01-1.718 0 1.159 1.159 0 01-.925-.793c.132.132.4.132.925.264 1.322.264 2.643-.264 2.907-1.322a13.663 13.663 0 01.4-1.586 8.422 8.422 0 00.925.264c-.132.529-.4 1.057-.529 1.718a3.737 3.737 0 01-3.7 2.511c-1.454 0-2.247-.925-3.3-1.718-.661-.529-1.322-1.189-1.982-1.718a14.62 14.62 0 01-4.758-2.379 9.045 9.045 0 003.568 2.775 34.584 34.584 0 01-1.718 6.343c-.264 1.057-2.775 5.154-3.568 5.55-.529.264-3.568 2.907-4.229 3.3a5.93 5.93 0 01-1.454 1.718c-1.982 1.057-3.3-.925-4.361-2.643-.529-.793-1.85-3.04-.661-3.7 1.057-.529 1.718-1.057 2.907-1.718a4.016 4.016 0 00.661.925c0-.4-.132-.661-.132-1.057a3.772 3.772 0 010-1.718c0-.529.132-1.189.132-1.718-.132.661-.529 1.189-.661 1.85a1.191 1.191 0 00-.132.661 21.353 21.353 0 01-7.665.132c-.132-.925-.4-1.982-.529-2.643v4.237a3.008 3.008 0 01-.529 2.114c-.4.793-.661.925-1.322 2.247a11.368 11.368 0 01-.132 2.114c-.4 1.322-3.965.264-4.89 0-1.189-.264-3.568-.793-3.04-2.379a19.168 19.168 0 001.189-4.758 25.648 25.648 0 01-4.493-11.1 13.782 13.782 0 01.529-6.476 17.58 17.58 0 014.625-7.268c3.04-2.643 5.815-3.7 10.308-4.361-1.057 1.189-2.114 2.511-3.3 3.832a20.478 20.478 0 00-2.643 4.229c-1.057 2.114-1.057 2.907.4 4.625 1.189 1.586 1.85 2.247 2.247 3.832a8.559 8.559 0 00-.661 2.775c1.454 1.586 2.511 2.643 3.832 2.907a5.118 5.118 0 003.7-.4c2.643-1.322 5.154-3.172 8.194-3.3 1.454-3.436 1.322-6.343.529-9.779a58.531 58.531 0 01-.793-6.74 17.227 17.227 0 00-.264 6.872c.529 2.907.925 6.079-.529 8.59-2.775.264-5.154 1.85-7.665 3.172a4.364 4.364 0 01-3.172.264c-.793-.132-1.454-.793-2.643-2.114a6.139 6.139 0 01.793-3.04 57.631 57.631 0 013.172-5.418c-1.322 1.718-2.643 3.172-3.7 4.758a12.324 12.324 0 00-1.982-3.172 2.784 2.784 0 01-.4-3.436 14.2 14.2 0 012.643-4.229c2.114-2.379 4.1-4.89 6.476-7.268a5.035 5.035 0 013.428-1.455c1.586-.264 3.04-.529 4.625-.925a26.978 26.978 0 01-4.493.4c1.454-1.85 2.247-2.907 4.625-3.965 5.815-2.511 9.515-2.775 14.008 1.057a31.639 31.639 0 003.436 2.775 5.816 5.816 0 00-1.322.264 5.038 5.038 0 011.982.132c.132.132.4.264.529.4a5.381 5.381 0 011.85 1.586 17.5 17.5 0 011.586 2.643c-.264-.132-.529-.132-.793-.264a.8.8 0 00-.529-.132 1.589 1.589 0 00-1.057.264 4.306 4.306 0 01-1.718.529 1.459 1.459 0 001.057 0h.132c-.132.132-.132.4-.264.661a2.249 2.249 0 00.132.925c0 .132.132.132.132.264-.264.132-.4.132-.661.264a12.736 12.736 0 013.172 0c.132.4.132.661.264 1.057h-.4a1.808 1.808 0 00-1.85-.132c-2.247.529-1.718 1.85-2.775 3.832 1.057-1.322 1.057-2.775 2.775-3.172.4-.132.661-.264.925-.132a2.593 2.593 0 00-1.189 1.189c-.529 1.454-.132 2.511-.793 3.832.661-1.189.661-2.247 1.322-3.568.264-.4 1.057-1.189 1.454-1.189h.4a12.866 12.866 0 01.132 2.114 57.563 57.563 0 01-.529 3.568 9.474 9.474 0 001.189-3.568 10 10 0 000-3.965c-.4-1.85 1.454-1.454 2.511-2.379.793-.661 1.322-1.586 1.982-2.247s1.85.264 2.114 1.057a26.308 26.308 0 011.454 10.572c-.4 3.3-1.982 7-4.89 8.59-3.7 2.114-8.194.793-11.894-.4a9.44 9.44 0 01-1.982-1.057 2.969 2.969 0 01.266 2.382zm-3.3 13.348c-.132 1.322-.529 1.454-1.85 1.454a27.623 27.623 0 01-3.3-.132 7.179 7.179 0 01-1.465-.27c1.189-.925 3.3-4.625 3.7-5.947s.925-2.511 1.189-3.832a7.451 7.451 0 00.529 1.586 7.821 7.821 0 01.661 2.511 25.464 25.464 0 00.132 3.172 2.045 2.045 0 01.4 1.455zm-38.589-27.488a2.109 2.109 0 00-.4 1.057c-.4 1.454.132 2.775-1.189 3.832.661 1.189.529 1.718 1.982 1.189a5.457 5.457 0 001.454-.925c-.132.529-.4 1.057-.529 1.586 0 .132 0 .132-.132.264-1.057.4-2.379.661-2.907-.4a6.543 6.543 0 01-.529-1.718c-1.718-1.716.793-4.095 2.246-4.888zm.132 1.586a.8.8 0 01.132-.529c0-.132 0-.132.132-.264.4.264.4.529.529 1.057-.268-.267-.532-.399-.797-.267zm1.322 15.462a31.234 31.234 0 003.568 7.665 9.105 9.105 0 01-.4 1.057c-1.057 1.454-3.7-.661-4.493-1.454a5.346 5.346 0 01-1.586-2.907c-.132-.661 0-.661.529-1.189l1.982-1.982zm50.347-21.808c0 .132.132.264.132.4l-.132.132c-.132-.132-.264-.4-.4-.529zm-49.161 8.061zm-2.114-3.172zm-3.3 5.022zm18.5 19.427zm32.246-9.779zm11.894-4.493z" fill="#1e1e1e"/>
    <path d="M560.558 185.835a13.744 13.744 0 00-1.982.264c0-.264-.132-.4-.132-.661a1.876 1.876 0 00-1.189-1.057c.4-.264.925-.529 1.322-.793-1.057.529-2.247.4-3.172.925-.793.529-1.85 2.247-2.643 2.907a11.024 11.024 0 001.586-1.057 2.45 2.45 0 00.264.925 2.082 2.082 0 00.925.925 4.134 4.134 0 00-.661 1.322 11.547 11.547 0 015.682-3.7zM551.043 183.853a5.216 5.216 0 013.3-4.1c-3.168.796-3.696 2.118-3.3 4.1zM556.2 198.919c-.132.4-.132 1.057-.264 1.454a5.72 5.72 0 01.661-1.586c.264-.529.4-.529.925-.793a12.28 12.28 0 001.322-.661c-.4 0-1.057.264-1.454.264-.929.132-1.061.397-1.19 1.322zM539.281 181.078c-1.189 1.189-2.247 5.022-2.643 6.608.529-1.322 1.982-4.89 3.04-5.815a2.765 2.765 0 01.793-.529c-.793 1.322-.661 1.586-.4 3.3a6.977 6.977 0 011.85-3.832c1.057-.264 2.114-.661 3.3-1.057-1.322.132-2.511.264-3.832.4-1.183.264-1.447.264-2.108.925z" fill="#1e1e1e"/>
    <path d="M555.008 187.818a.887.887 0 011.586-.793v.132a8.551 8.551 0 00-1.189 1.057.422.422 0 01-.4-.4" fill="#fffacb"/>
    <text fill="#5b5b5b" font-family="SegoeUI, Segoe UI" font-size="14" transform="translate(490.961 247.657)">
        Azu<tspan letter-spacing="-.013em" x="23.283" y="0">r</tspan><tspan x="27.966" y="0">e HD Insight</tspan><tspan x="20.665" y="16.8">(Anal</tspan><tspan letter-spacing=".003em" x="52.356" y="16.8">y</tspan><tspan x="59.172" y="16.8">tics)</tspan>
    </text>
    <path fill="none" stroke="#969696" stroke-miterlimit="10" stroke-width="1.5" d="M286.343 40v162h34.465"/>
    <path fill="#969696" d="M319.276 207.236l9.067-5.236-9.067-5.236v10.472z"/>
    <path fill="none" stroke="#969696" stroke-miterlimit="10" stroke-width="1.5" d="M456.343 40v162h34.465"/>
    <path fill="#969696" d="M489.276 207.236l9.067-5.236-9.067-5.236v10.472z"/>
    <path fill="none" stroke="#969696" stroke-miterlimit="10" stroke-width="1.5" d="M490.54 40.03h-81.265"/>
    <path fill="#969696" d="M489.008 34.794l9.067 5.236-9.067 5.236V34.794z"/>
    <path fill="none" stroke="#969696" stroke-miterlimit="10" stroke-width="1.5" d="M199.675 157.895V102.63"/>
    <path fill="#969696" d="M204.91 156.363l-5.235 9.067-5.236-9.067h10.471z"/>
    <path d="M348.665 7.418v41.411c0 4.359 9.738 7.8 21.678 7.8V7.418z" fill="#3998c5"/>
    <path d="M370.343 56.48h.34c11.867 0 21.338-3.431 21.338-7.777V7.418h-21.678z" fill="#59b3d8"/>
    <path d="M391.682 7.8c0 4.246-9.636 7.8-21.451 7.8s-21.566-3.556-21.566-7.8S358.3 0 370.116 0s21.566 3.556 21.566 7.8" fill="#fff"/>
    <path d="M387.318 7.341c0 2.868-7.685 5.162-17.092 5.162s-17.2-2.293-17.2-5.162 7.685-5.162 17.092-5.162 17.2 2.294 17.2 5.162" fill="#7fb900"/>
    <path d="M383.651 10.438c2.294-.912 3.556-1.95 3.556-3.1 0-2.868-7.685-5.162-17.092-5.162s-17.092 2.294-17.092 5.162c0 1.147 1.376 2.294 3.556 3.1 3.1-1.262 8.029-1.95 13.536-1.95a41.81 41.81 0 0113.536 1.95" fill="#b7d332"/>
    <path d="M382.261 38.559c-3.414.7-3.649-.456-3.649-.456 3.6-5.349 5.112-12.138 3.811-13.8-3.547-4.532-9.692-2.389-9.79-2.333l-.033.006a12.176 12.176 0 00-2.28-.237 5.628 5.628 0 00-3.605 1.079s-10.955-4.513-10.446 5.674c.114 2.166 3.107 16.4 6.683 12.1 1.307-1.572 2.57-2.9 2.57-2.9a3.316 3.316 0 002.166.553l.062-.051a2.387 2.387 0 00.025.613c-.921 1.026-.651 1.21-2.493 1.589-1.863.384-.767 1.067-.055 1.246a3.786 3.786 0 004.226-1.368l-.055.217a6.157 6.157 0 01.57 3.326 9.172 9.172 0 00.213 3.206c.284.773.57 2.514 2.989 2a3.571 3.571 0 003.217-3.431c.1-1.331.342-1.14.352-2.326l.188-.563c.217-1.806.034-2.389 1.279-2.117l.3.026a6.9 6.9 0 002.823-.475c1.518-.7 2.417-1.88.921-1.571z" fill="#336790"/>
    <path d="M367.85 29.623a1.453 1.453 0 00-.494-.154 1.058 1.058 0 00-.727.1.265.265 0 00-.114.177c-.032.228.307.657.731.716a.78.78 0 00.1.007.8.8 0 00.723-.464l.011-.04c.02-.071.001-.215-.23-.342zM377.284 29.267a1.356 1.356 0 00-.49-.01c-.355.051-.7.21-.669.42l.006.021a.723.723 0 00.659.423.74.74 0 00.093-.006.864.864 0 00.486-.267.555.555 0 00.184-.371c-.018-.098-.114-.177-.269-.21z" fill="#fff"/>
    <path d="M383.293 38.515c-.164-.5-.883-.353-1.119-.3-2.4.5-3.079.007-3.219-.131a28.037 28.037 0 003.721-8.365c.665-2.66.652-4.771-.029-5.641a7.776 7.776 0 00-6.043-2.987 11.694 11.694 0 00-4.042.539l-.029.007-.046.016-.041.016a9.41 9.41 0 00-2.14-.278 6.073 6.073 0 00-3.619 1.026 15.831 15.831 0 00-3.461-.87 7.157 7.157 0 00-5.116.921c-1.586 1.125-2.322 3.147-2.179 6.007.07 1.349 2.043 12.093 5.141 13.127a1.893 1.893 0 002.1-.835 56.095 56.095 0 012.394-2.7 3.779 3.779 0 001.8.479 1.619 1.619 0 00.015.19 7.245 7.245 0 00-.325.4c-.414.527-.512.651-1.854.928-.544.114-1.268.324-1.279.863s.746.878 1.193.989a4.075 4.075 0 004.154-1.006 27.674 27.674 0 00.4 6.385 2.973 2.973 0 002.855 2.2 4.586 4.586 0 00.953-.108A3.611 3.611 0 00376.8 46c.2-1.14.539-3.912.684-5.307a3.518 3.518 0 001.279.194 7.076 7.076 0 002.686-.506c.851-.407 2.051-1.23 1.844-1.866zM377.188 40c-.059.779-.509 4.531-.743 5.892a3.017 3.017 0 01-2.836 2.872 2.4 2.4 0 01-3.04-1.51q-.033-.1-.058-.2a33.7 33.7 0 01-.331-7.441.3.3 0 00-.032-.139 1.608 1.608 0 00-.058-.285 1.568 1.568 0 00-.77-.933l-.038-.019a1.14 1.14 0 00-.993-.059 8.076 8.076 0 01.409-1.3l.064-.171c.073-.2.161-.391.255-.607.5-1.117 1.19-2.645.441-6.107a2.106 2.106 0 00-2.421-1.735q-.063.01-.125.025a6.209 6.209 0 00-2.408.859 9.229 9.229 0 012.115-5.633 5.223 5.223 0 013.939-1.482 8.125 8.125 0 015.929 2.589 9.613 9.613 0 012.166 3.558c-1.627-.195-2.721.1-3.259.865-1.14 1.637.665 4.881 1.535 6.441.148.266.3.54.35.657a5.764 5.764 0 00.921 1.463 3.114 3.114 0 01.307.424l-.074.021c-.461.124-1.322.366-1.244 1.945zm-15.973.844c-1.02-.336-2.152-2.385-3.188-5.757a36.834 36.834 0 01-1.444-6.588c-.129-2.588.5-4.395 1.882-5.371a5.59 5.59 0 013.257-.876 14.088 14.088 0 014.25.772 2.63 2.63 0 00-.2.18c-2.368 2.39-2.284 6.494-2.28 6.666v.02a19.726 19.726 0 01-.069 3.839 4.221 4.221 0 001.112 3.534 3.679 3.679 0 00.378.336 58.987 58.987 0 00-2.309 2.615c-.48.574-.937.779-1.393.628zm3.423-7a20.524 20.524 0 00.08-3.939 4.8 4.8 0 013.193-1 1.382 1.382 0 011.162 1.209c.7 3.26.092 4.622-.4 5.718-.095.211-.193.429-.274.644l-.064.171a10.027 10.027 0 00-.412 1.265 3.1 3.1 0 01-2.327-.99 3.678 3.678 0 01-.957-3.084zm3.347 5.14a.307.307 0 00.03-.038.523.523 0 01.7-.169l.051.026a.959.959 0 01.416 1.254 3.479 3.479 0 01-3.893 1.254 1.674 1.674 0 01-.729-.358 1.746 1.746 0 01.767-.276c1.5-.307 1.71-.509 2.22-1.154.114-.146.255-.325.445-.536zm9.612-3.093c-.059-.145-.192-.381-.374-.709l-.008-.014c-.745-1.335-2.488-4.462-1.568-5.778a2.085 2.085 0 011.807-.656 7.5 7.5 0 01.987.074 8.153 8.153 0 01-.124 1.31 10.892 10.892 0 00-.148 1.387 10.416 10.416 0 00.114 1.571 5.552 5.552 0 01-.352 3.451 4.186 4.186 0 01-.333-.64zm4.156-5.685a31.493 31.493 0 01-3.267 7.253 4.028 4.028 0 00-.194-.251l-.073-.093-.021-.025a5.827 5.827 0 00.57-4.1 9.9 9.9 0 01-.1-1.467 10.483 10.483 0 01.143-1.316 7.952 7.952 0 00.13-1.6.523.523 0 00.017-.2 9.767 9.767 0 00-5.594-6.4c5.106-1.247 7.754 1.3 8.666 2.456.684.87.583 2.911-.273 5.746zm-3.408 8.438a1.837 1.837 0 00.228-.075 1.544 1.544 0 00.16.122 5.1 5.1 0 003.576.13 1.95 1.95 0 01.328-.043 4.073 4.073 0 01-1.444 1.026 5.6 5.6 0 01-3.561.263c-.062-.036-.075-.063-.076-.07-.064-1.108.371-1.23.8-1.349z" fill="#fff"/>
    <path d="M348.665 171.418v41.411c0 4.359 9.738 7.8 21.678 7.8v-49.211z" fill="#3998c5"/>
    <path d="M370.343 220.48h.34c11.867 0 21.338-3.431 21.338-7.777v-41.285h-21.678z" fill="#59b3d8"/>
    <path d="M391.682 171.8c0 4.246-9.636 7.8-21.451 7.8s-21.566-3.556-21.566-7.8 9.636-7.8 21.451-7.8 21.566 3.556 21.566 7.8" fill="#fff"/>
    <path d="M387.318 171.341c0 2.868-7.685 5.162-17.092 5.162s-17.2-2.293-17.2-5.162 7.685-5.162 17.092-5.162 17.2 2.294 17.2 5.162" fill="#7fb900"/>
    <path d="M383.651 174.438c2.294-.912 3.556-1.95 3.556-3.1 0-2.868-7.685-5.162-17.092-5.162s-17.092 2.294-17.092 5.162c0 1.147 1.376 2.294 3.556 3.1 3.1-1.262 8.029-1.95 13.536-1.95a41.81 41.81 0 0113.536 1.95" fill="#b7d332"/>
    <path d="M382.261 202.559c-3.414.7-3.649-.456-3.649-.456 3.6-5.349 5.112-12.138 3.811-13.8-3.547-4.532-9.692-2.389-9.79-2.333l-.033.006a12.176 12.176 0 00-2.28-.237 5.628 5.628 0 00-3.605 1.079s-10.955-4.513-10.446 5.674c.114 2.166 3.107 16.4 6.683 12.1 1.307-1.572 2.57-2.9 2.57-2.9a3.316 3.316 0 002.166.553l.062-.051a2.387 2.387 0 00.025.613c-.921 1.026-.651 1.21-2.493 1.589-1.863.384-.767 1.067-.055 1.246a3.786 3.786 0 004.226-1.368l-.055.217a6.157 6.157 0 01.57 3.326 9.172 9.172 0 00.213 3.206c.284.773.57 2.514 2.989 2a3.571 3.571 0 003.217-3.431c.1-1.331.342-1.14.352-2.326l.188-.563c.217-1.806.034-2.389 1.279-2.117l.3.026a6.9 6.9 0 002.823-.475c1.518-.7 2.417-1.88.921-1.571z" fill="#336790"/>
    <path d="M367.85 193.623a1.453 1.453 0 00-.494-.154 1.058 1.058 0 00-.727.1.265.265 0 00-.114.177c-.032.228.307.657.731.716a.78.78 0 00.1.007.8.8 0 00.723-.464l.011-.04c.02-.071.001-.215-.23-.342zM377.284 193.267a1.356 1.356 0 00-.49-.01c-.355.051-.7.21-.669.42l.006.021a.723.723 0 00.659.423.74.74 0 00.093-.006.864.864 0 00.486-.267.555.555 0 00.184-.371c-.018-.098-.114-.177-.269-.21z" fill="#fff"/>
    <path d="M383.293 202.515c-.164-.5-.883-.353-1.119-.3-2.4.5-3.079.007-3.219-.131a28.037 28.037 0 003.721-8.365c.665-2.66.652-4.771-.029-5.641a7.776 7.776 0 00-6.043-2.987 11.694 11.694 0 00-4.042.539l-.029.007-.046.016-.041.016a9.41 9.41 0 00-2.14-.278 6.073 6.073 0 00-3.619 1.026 15.831 15.831 0 00-3.461-.87 7.157 7.157 0 00-5.116.921c-1.586 1.125-2.322 3.147-2.179 6.007.07 1.349 2.043 12.093 5.141 13.127a1.893 1.893 0 002.1-.835 56.095 56.095 0 012.394-2.7 3.779 3.779 0 001.8.479 1.619 1.619 0 00.015.19 7.245 7.245 0 00-.325.4c-.414.527-.512.651-1.854.928-.544.114-1.268.324-1.279.863s.746.878 1.193.989a4.075 4.075 0 004.154-1.006 27.674 27.674 0 00.4 6.385 2.973 2.973 0 002.855 2.2 4.586 4.586 0 00.953-.108A3.611 3.611 0 00376.8 210c.2-1.14.539-3.912.684-5.307a3.518 3.518 0 001.279.194 7.076 7.076 0 002.686-.506c.851-.407 2.051-1.23 1.844-1.866zm-6.1 1.482c-.059.779-.509 4.531-.743 5.892a3.017 3.017 0 01-2.836 2.872 2.4 2.4 0 01-3.04-1.51q-.033-.1-.058-.2a33.7 33.7 0 01-.331-7.441.3.3 0 00-.032-.139 1.608 1.608 0 00-.058-.285 1.568 1.568 0 00-.77-.933l-.038-.019a1.14 1.14 0 00-.993-.059 8.076 8.076 0 01.409-1.3l.064-.171c.073-.2.161-.391.255-.607.5-1.117 1.19-2.645.441-6.107a2.106 2.106 0 00-2.421-1.735q-.063.01-.125.025a6.209 6.209 0 00-2.408.859 9.229 9.229 0 012.115-5.633 5.223 5.223 0 013.939-1.482 8.125 8.125 0 015.929 2.589 9.613 9.613 0 012.166 3.558c-1.627-.195-2.721.1-3.259.865-1.14 1.637.665 4.881 1.535 6.441.148.266.3.54.35.657a5.764 5.764 0 00.918 1.474 3.114 3.114 0 01.307.424l-.074.021c-.461.124-1.322.366-1.244 1.945zm-15.973.844c-1.02-.336-2.152-2.385-3.188-5.757a36.834 36.834 0 01-1.444-6.588c-.129-2.588.5-4.395 1.882-5.371a5.59 5.59 0 013.257-.876 14.088 14.088 0 014.25.772 2.63 2.63 0 00-.2.18c-2.368 2.39-2.284 6.494-2.28 6.666v.02a19.726 19.726 0 01-.069 3.839 4.221 4.221 0 001.112 3.534 3.679 3.679 0 00.378.336 58.987 58.987 0 00-2.309 2.615c-.48.574-.937.779-1.393.628zm3.423-7a20.524 20.524 0 00.08-3.939 4.8 4.8 0 013.193-1 1.382 1.382 0 011.162 1.209c.7 3.26.092 4.622-.4 5.718-.095.211-.193.429-.274.644l-.064.171a10.027 10.027 0 00-.412 1.265 3.1 3.1 0 01-2.327-.99 3.678 3.678 0 01-.957-3.084zm3.347 5.14a.307.307 0 00.03-.038.523.523 0 01.7-.169l.051.026a.959.959 0 01.416 1.254 3.479 3.479 0 01-3.893 1.254 1.674 1.674 0 01-.729-.358 1.746 1.746 0 01.767-.276c1.5-.307 1.71-.509 2.22-1.154.114-.146.255-.325.445-.536zm9.612-3.093c-.059-.145-.192-.381-.374-.709l-.008-.014c-.745-1.335-2.488-4.462-1.568-5.778a2.085 2.085 0 011.807-.656 7.5 7.5 0 01.987.074 8.153 8.153 0 01-.124 1.31 10.892 10.892 0 00-.148 1.387 10.416 10.416 0 00.114 1.571 5.552 5.552 0 01-.352 3.451 4.186 4.186 0 01-.333-.64zm4.156-5.685a31.493 31.493 0 01-3.267 7.253 4.028 4.028 0 00-.194-.251l-.073-.093-.021-.025a5.827 5.827 0 00.57-4.1 9.9 9.9 0 01-.1-1.467 10.483 10.483 0 01.143-1.316 7.952 7.952 0 00.13-1.6.523.523 0 00.017-.2 9.767 9.767 0 00-5.594-6.4c5.106-1.247 7.754 1.3 8.666 2.456.684.87.583 2.911-.273 5.746zm-3.408 8.438a1.837 1.837 0 00.228-.075 1.544 1.544 0 00.16.122 5.1 5.1 0 003.576.13 1.95 1.95 0 01.328-.043 4.073 4.073 0 01-1.444 1.026 5.6 5.6 0 01-3.561.263c-.062-.036-.075-.063-.076-.07-.064-1.108.371-1.23.8-1.349z" fill="#fff"/>
</svg>

