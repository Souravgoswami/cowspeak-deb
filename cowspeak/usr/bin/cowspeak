#!/usr/bin/ruby -W0
# Written by Sourav Goswami
# The GNU General Public License v3.0

require 'io/console'

Help = -> {
	puts <<EOF
Help:
	Hi, my name is font generator, also known as fgen.
	I am a funny, little program who generates a font of your choice on your terminal!

	Usage:
		1. When you run me, I will ask you to choose a font style template.
		2. Select a template of your choice, and then start typing, I will show you what you
		   typed in your style.
		3. When done, press escape key or ctrl + c or ctrl + k to quit me.
		4. You can also pass arguments to me, I will show them but you need to confirm the style.
			Example:
				./#{__FILE__} This is just a sample text!!

		I will handle the arguments (fgen <your texts>). I will also ask you for a style.

		Available Arguments:
			--help				this help
			--blink				blink the text typed
			--colour			show a random coloured text

		Keys to navigate around and control the texts:
			backspace		delete the character before the cursor
			ctrl + w			go up from the cursor
			ctrl + s			go down from the cursor
			ctrl + a			go to the left from the cursor
			ctrl + d			go to the right from the cursor
			ctrl + space			delete the character under the cursor from the cursor
			ctrl + r			clear the input
			ctrl + l			clear the input
			ctrl + k			exit prompt
			ctrl + c			exit prompt

		Suggestion: This program uses UTF-8 fonts, and can be copied to use them on the web (if supported).
EOF
	exit! 0
}

def check_args
	if ARGV.include?('--help')
		Help.call
		ARGV.delete('--help')
	end

	if ARGV.include?('--blink')
		@blink = true
		ARGV.delete('--blink')
	else
		@blink = false
	end

	if ARGV.include?('--colour') then
		@coloured = true
		ARGV.delete('--colour')
	else
		@coloured = false
	end

	main
end

at_exit { puts "\033[0m" }

def main
	begin
		gen = ->(font, ch) {
					('a'..'z').each do |c|
						return font if c == ch
						font = font.succ
					end
		}

		fonts = ["\x61\x00", "\xf0\x9d\x93\xaa" ,"\xf0\x9d\x90\x9a", "\xf0\x9d\x9a\x8a", "\xf0\x9d\x96\xba",
				"\x61\xcc\xbd\xcd\x90", "\x61\xcc\xbd\xcd\x91", "\x61\xcc\xbd\xcd\x92",
				"\x61\xcc\xbd\xcd\x93", "\x61\xcc\xbd\xcd\x94", "\x61\xcc\xbd\xcd\x95",
				"\x61\xcc\xbd\xcd\x96", "\x61\xcc\xbd\xcd\x97", "\x61\xcc\xbd\xcd\x98",
				"\x61\xcc\xbd\xcd\x99", "\xf0\x9f\x85\x90", "\xf0\x9f\x85\xb0", "\xf0\x9f\x84\xb0",
				"\xf0\x9d\x94\x9e", "\xf0\x9d\x96\x86", "\x61\xcd\x80", "\x61\xcd\x81", "\x61\xcd\x82",
				"\x61\xcd\x83", "\x61\xcd\x84", "\x61\xcd\x85", "\x61\xcd\x86", "\x61\xcd\x87", "\x61\xcd\x88",
				"\x61\xcd\x89", "\x61\xcc\xba", "\x61\xcc\xbb", "\x61\xcc\xbc", "\x61\xcc\xbd", "\x61\xcc\xbe",
				"\x61\xcc\xbf", "\x61\xcc\x9f", "\xf0\x9d\x95\x92", "\x61\xd2\x89", "\x61\xcc\xb0",
				"\x61\xcc\xb1", "\x61\xcc\xb2", "\x61\xcc\xb3", "\x61\xcc\xb4",
				"\x61\xcc\xb5", "\x61\xcc\xb6", "\x61\xcc\xb7", "\x61\xcc\xb8", "\x61\xcc\xb9" ]


		print "\033[0m"
		puts "The Available Styles are:\n\n"
		fonts.size.times do |count| print "\t#{count + 1} "
			('a'..'z').map do |c| print gen.call(fonts[count], c) end
			puts
		end
		puts "\t#{fonts.size + 1} Random"

		print "\nSelect any Style(from 1 to #{fonts.size + 1}): "
		choice = STDIN.gets.to_i
		random = ((choice > fonts.size) || (choice < 1)) ? true : false
		font, word = fonts[choice - 1], ''

		if ARGV.empty?
			puts "Start Typing!..."
			loop do
				w = STDIN.getch
				raise Interrupt if ["\u0003", "\v"].include?(w)	# ctrl + c / ctrl + k => exit prompt

				word += "\033[38;5;#{rand(0..230)}m" if @coloured	# colour flag used
				word += "\033[5m" if @blink				# blink flag used

				if w == "\u007F" then word += "\b\s\e[D"		# backspace => delete
					elsif w == "\r" then word += "\n"		# enter => "\n"
					elsif w == "\u0017" then word += "\e[A"		# ctrl + w => up
					elsif w == "\u0013" then word += "\e[B"		# ctrl + s => down
					elsif w == "\u0001" then word += "\e[D"		# ctrl + a => left
					elsif w == "\u0004" then word += "\e[C"		# ctrl + d => right
					elsif w == "\u0000" then word += "\s\b"		# ctrl + space => delete
					elsif w == "\u0012" then word = '' 		# ctrl + r => clear
					elsif w == "\f" then word = ''			# ctrl + l => clear
				else
					word += "#{w =~ /[a-z]/ ? gen.call(font, w) : w }" unless random
					word += "#{w =~ /[a-z]/ ? gen.call(fonts.sample, w) : w }" if random
				end

				print "\033[H\033[J#{word}"
			end
		else
			ARGV.each do |word|
				word.chars do |w|
					print "\033[38;5;#{rand(0..230)}m" if @coloured
					print "\033[5m" if @blink
					print(w =~ /[a-z]/ ? gen.call(font, w) : w) unless random
					print(w =~ /[a-z]/ ? gen.call(fonts.sample, w) : w) if random
				end
				print(' ')
			end
		end
	rescue Interrupt
		print "\n\033[0mExit now? (Y/n) "
		retry if STDIN.gets.downcase.include?('n')
		exit 0
	rescue Exception => e
		puts "\033[0mUh oh, #{__FILE__} crashed\nWhat would you like to do?\n
			1. Exit
			2. Retry
			3. Show Help
			4. Show Error Details
			5. Save Error Details to #{Dir.pwd}/error.log
			6. Contact Developer
			Default Exit"
		case STDIN.gets.to_i
			when 2 then retry
			when 3 then Help.call
			when 4 then puts e
			when 5 then File.open('error.log', 'a') { |f| f.puts e }
			when 6 then
				puts "please contact <souravgoswami@protonmail.com> and tell him about #{e} for #{__FILE__}"
			else exit! 127
		end
	end
end

check_args
