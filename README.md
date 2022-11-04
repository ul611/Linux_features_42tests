## Linux_features_42tests

_Некоторые особенности написания кода и запуска популярных юнит-тестов проектов Libft, Get Next Line (GNL), Ft_printf на Linux._

**0.** Некоторые man на MacOS отличаются от man на Linux. В основном, отличия незначительны, 
но лучше гуглить "man macOS <функция>", чтобы ничего не упустить (или не сделать лишнего).

Например, в функции calloc() для Linux указано дополнительное ограничение на максимальный
размер выделяемой памяти (If the multiplication of nmemb and size would result in integer 
overflow, then calloc() returns an error), чего нет в мануале для Mac.

Первая ссылка в гугле будет выглядеть примерно так:
https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man3/calloc.3.html

### Проекты.

#### 1. Libft

**1.1.** 	https://github.com/jtoty/Libftest
		
		Максимально дружелюбный тест.

**1.2.**	https://github.com/alelievr/libft-unit-test
		
		для данного теста:
		
		- добавляем правило so в Makefile (его не обязательно удалять перед сдачей проекта),
		например, такое:
		
		so:			$(OBJS) $(OBJSBONUS) $(HDR)
					gcc -fPIC $(FLAGS) -c $(SRCSBONUS) $(SRCS)
					gcc -shared -o libft.so $(OBJS) $(OBJSBONUS)
		
		- устанавливаем пакеты clang, build-essential, autoconf, libncurses-dev, libbsd-dev.
		
**1.3.**	Стандартно стоит проверить проект на утечки, например, при помощи valgrind
		
		Стоит иметь в виду, что прохождение данных тестов не может гарантировать успешной сдачи либы.
		
		Спойлер: как Мулинетт, так и тесты, очень поверхностно проверяют бонусную часть. 


#### 2. Get next line

**2.1.**	https://github.com/mrjvs/42cursus_gnl_tests
		
		Максимально дружелюбный тест.
		
**2.2.**	https://github.com/charMstr/GNL_lover
		
		Тест, прохождение которого на Линуксе практически гарантирует вам успешную сдачу проекта Мулинетт.
		
**2.3.**	
		
		Еще раз проверить все на утечки при помощи valgrind


#### 3. Ft_printf

		Скорее всего, любой тест, который вы захотите запустить, запустится.
		Из-за определенных особенностей вывода стандартного printf на Линуксе, некоторые тестовые случаи будут фейлиться.
		
		Например, стандартный printf на Линуксе нулевой %p выводит как (nil), а Mac - как 0x0.
		Для нулевого %s на Mac считается, что была передана строка (null).
		
		Вы можете сравнить дифф, представленный ниже, с диффом вашего проекта.
		Если они совпадают, то все хорошо, и на Mac ваша функция пройдет тест как надо.

**3.1.**	https://github.com/Mazoise/42TESTERS-PRINTF
		
		См. файл 42TESTERS-PRINTF_diff_for_Linux.txt
		
**3.2.**	https://github.com/gavinfielder/pft

		См. файл ptf_results_for_Linux.txt
		Номера тестов, которые фейлятся (их можно отключить): 7 8 9 10 91 113 114 117 118 173 178 647 4192 4193 4194 4205 4206
		
**3.3.**	https://github.com/cacharle/ft_printf_test
		
		См. файл ft_printf_test_result_for_Linux.log

По вопросам и предложениям улучшения статьи: 

- slack: @twilford

Отдельную благодарность хочется выразить всем создателям указанных тестов <3
