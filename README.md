<div align="center">

# 📚 Libft

**My very first C library, written from scratch at School 42**

![Language](https://img.shields.io/badge/language-C-blue?style=for-the-badge&logo=c)
![School](https://img.shields.io/badge/school-42-black?style=for-the-badge)
![Norminette](https://img.shields.io/badge/norminette-passing-success?style=for-the-badge)
![Bonus](https://img.shields.io/badge/bonus-included-brightgreen?style=for-the-badge)

</div>

---

## 📖 Table of Contents

- [About](#-about)
- [Features](#-features)
  - [Part 1: Libc Functions](#part-1--libc-functions)
  - [Part 2: Additional Functions](#part-2--additional-functions)
  - [Bonus: Linked Lists](#bonus--linked-lists)
- [Installation](#-installation)
- [Usage](#-usage)
- [Makefile Commands](#-makefile-commands)
- [Project Structure](#-project-structure)
- [Testing](#-testing)
- [What I Learned](#-what-i-learned)
- [Author](#-author)

---

## 🧠 About

**Libft** is the first project of the 42 Common Core. The goal is to rebuild a set of functions from the C standard library, plus some extra utilities, and package them as a static library (`libft.a`) that I can reuse in later 42 projects such as `ft_printf`, `get_next_line`, `push_swap` and `minishell`.

Every function is written from scratch under these rules:

- ✅ Written in C and compiled with `-Wall -Wextra -Werror`
- ✅ Follows the [42 Norm](https://github.com/42School/norminette) coding standard
- ✅ No global variables
- ✅ The only standard library functions allowed are `malloc`, `free` and `write`
- ✅ No memory leaks, no crashes (segfaults, bus errors, double frees)

---

## ✨ Features

### Part 1: Libc Functions

Reimplementations of standard libc functions, with the same behaviour as the originals.

| Category | Function | Description |
|:--|:--|:--|
| **Character checks** | `ft_isalpha` | Checks for an alphabetic character |
| | `ft_isdigit` | Checks for a digit (0–9) |
| | `ft_isalnum` | Checks for an alphanumeric character |
| | `ft_isascii` | Checks whether a value fits in 7-bit ASCII |
| | `ft_isprint` | Checks for a printable character |
| **Character conversion** | `ft_toupper` | Converts a lowercase letter to uppercase |
| | `ft_tolower` | Converts an uppercase letter to lowercase |
| **Strings** | `ft_strlen` | Returns the length of a string |
| | `ft_strlcpy` | Size-bounded string copy |
| | `ft_strlcat` | Size-bounded string concatenation |
| | `ft_strchr` | Finds the first occurrence of a character |
| | `ft_strrchr` | Finds the last occurrence of a character |
| | `ft_strncmp` | Compares up to `n` characters of two strings |
| | `ft_strnstr` | Finds a substring within the first `len` bytes |
| | `ft_strdup` | Duplicates a string into newly allocated memory |
| **Memory** | `ft_memset` | Fills memory with a constant byte |
| | `ft_bzero` | Zeroes a block of memory |
| | `ft_memcpy` | Copies a memory area |
| | `ft_memmove` | Copies a memory area, handling overlap |
| | `ft_memchr` | Scans memory for a byte |
| | `ft_memcmp` | Compares two memory areas |
| | `ft_calloc` | Allocates zero-initialised memory |
| **Conversion** | `ft_atoi` | Converts a string to an `int` |

### Part 2: Additional Functions

Utility functions that are not in libc (or behave differently), and that come in handy in later projects.

| Function | Prototype | Description |
|:--|:--|:--|
| `ft_substr` | `char *ft_substr(char const *s, unsigned int start, size_t len)` | Extracts a substring |
| `ft_strjoin` | `char *ft_strjoin(char const *s1, char const *s2)` | Joins two strings into a new one |
| `ft_strtrim` | `char *ft_strtrim(char const *s1, char const *set)` | Trims characters in `set` from both ends |
| `ft_split` | `char **ft_split(char const *s, char c)` | Splits a string by a delimiter into a `NULL`-terminated array |
| `ft_itoa` | `char *ft_itoa(int n)` | Converts an `int` to a string |
| `ft_strmapi` | `char *ft_strmapi(char const *s, char (*f)(unsigned int, char))` | Applies `f` to each character and returns a new string |
| `ft_striteri` | `void ft_striteri(char *s, void (*f)(unsigned int, char *))` | Applies `f` to each character in place |
| `ft_putchar_fd` | `void ft_putchar_fd(char c, int fd)` | Writes a character to a file descriptor |
| `ft_putstr_fd` | `void ft_putstr_fd(char *s, int fd)` | Writes a string to a file descriptor |
| `ft_putendl_fd` | `void ft_putendl_fd(char *s, int fd)` | Writes a string and a newline to a file descriptor |
| `ft_putnbr_fd` | `void ft_putnbr_fd(int n, int fd)` | Writes an integer to a file descriptor |

### Bonus: Linked Lists

Functions for working with a singly linked list, built on this struct:

```c
typedef struct s_list
{
	void			*content;
	struct s_list	*next;
}	t_list;
```

| Function | Description |
|:--|:--|
| `ft_lstnew` | Creates a new node |
| `ft_lstadd_front` | Adds a node to the start of the list |
| `ft_lstadd_back` | Adds a node to the end of the list |
| `ft_lstsize` | Counts the nodes in the list |
| `ft_lstlast` | Returns the last node |
| `ft_lstdelone` | Frees one node's content and the node itself |
| `ft_lstclear` | Frees every node in the list |
| `ft_lstiter` | Applies a function to each node's content |
| `ft_lstmap` | Builds a new list by applying a function to each node |

---

## ⚙️ Installation

### Requirements

- A C compiler (`cc`, `gcc` or `clang`)
- `make`
- `ar` (included with binutils)

### Build

```bash
# Clone the repository
git clone https://github.com/rasiolisufaj/42-libft.git
cd 42-libft

# Build the mandatory part
make

# Or build everything, including the linked-list bonus
make bonus
```

Either command creates the static library `libft.a` in the repository root.

---

## 🚀 Usage

Include the header in your source file:

```c
#include "libft.h"

int	main(void)
{
	char	**words;
	int		i;

	words = ft_split("hello 42 world", ' ');
	i = 0;
	while (words[i])
	{
		ft_putendl_fd(words[i], 1);
		free(words[i]);
		i++;
	}
	free(words);
	ft_putnbr_fd(ft_atoi("  -2147483648"), 1);
	ft_putchar_fd('\n', 1);
	return (0);
}
```

Compile it and link against `libft.a`:

```bash
cc -Wall -Wextra -Werror main.c -I path/to/libft -L path/to/libft -lft -o program
./program
```

Output:

```
hello
42
world
-2147483648
```

---

## 🛠 Makefile Commands

| Command | Description |
|:--|:--|
| `make` / `make all` | Compiles the mandatory functions into `libft.a` |
| `make bonus` | Compiles the mandatory and bonus functions into `libft.a` |
| `make clean` | Removes object files (`*.o`) |
| `make fclean` | Removes object files and `libft.a` |
| `make re` | Runs `fclean`, then `all` |

---

## 🗂 Project Structure

```
42-libft/
├── Makefile
├── libft.h              # Prototypes and the t_list struct
├── ft_is*.c             # Character checks
├── ft_to*.c             # Character conversion
├── ft_str*.c            # String functions
├── ft_mem*.c            # Memory functions
├── ft_put*_fd.c         # Output to file descriptors
├── ft_atoi.c, ft_itoa.c, ft_split.c, ft_substr.c, ft_calloc.c, ft_bzero.c
└── ft_lst*_bonus.c      # Linked-list bonus
```

---

## 🧪 Testing

These community testers work well for checking the library:

- [libftTester](https://github.com/Tripouille/libftTester) by Tripouille
- [libft-unit-test](https://github.com/alelievr/libft-unit-test) by alelievr
- [francinette](https://github.com/xicodomingues/francinette) by xicodomingues

To check that the code follows the Norm:

```bash
norminette *.c libft.h
```

---

## 💡 What I Learned

- How core libc functions work internally, and their edge cases (`memmove` overlap, `strlcat` return values, `atoi` overflow)
- Manual memory management with `malloc` and `free`, and how to avoid leaks
- Pointer arithmetic and working with `void *` for generic memory
- Function pointers, used in `ft_strmapi`, `ft_striteri` and the `ft_lst*` functions
- Building static libraries with `ar` and writing a Makefile with sensible rules
- Writing clean, consistent code under the strict 42 Norm

---

## 👤 Author

**Rasiol Isufaj** (42 login: `raisufaj`)

[![GitHub](https://img.shields.io/badge/GitHub-rasiolisufaj-181717?style=flat&logo=github)](https://github.com/rasiolisufaj)

<div align="center">

⭐ If this repository helped you, consider giving it a star!

</div>
