<img width="642" height="301" alt="EPAT_Completed_Guided_Project_2 - Intern_Complete" src="https://github.com/user-attachments/assets/434fa8c8-d3cf-4207-bb6d-e587e3e7cbb6" />
[May2023_MiniProject_strategy_using_futures_OI.ipynb](https://github.com/user-attachments/files/23829619/May2023_MiniProject_strategy_using_futures_OI.ipynb)
{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "iBQkLGzb8k24"
   },
   "source": [
    "# **Welcome to the EPAT guided mini-project # 4! (Solution)**\n",
    "\n",
    "#### Date created: 9 April 2023\n",
    "#### Last updated on: 8 May 2023\n",
    "#### Created by: Saaransh Marwah and Jose Carlos Gonzales Tanaka\n",
    "#### Reviewed by: Vivek Krishnamoorthy"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "SJ0Zjg_-9hZu"
   },
   "source": [
    "<div class=\"alert alert-warning \">\n",
    "EPAT-guided projects aim to give you a flavor of solving a real-world problem using Python.  \n",
    "    \n",
    "Here's what we'll do.\n",
    "\n",
    "- We'll give you a step-wise process to follow so that you understand how to analyze a problem and break it down into steps.\n",
    "- We'll provide hints for the complicated steps. You can use them if you get stuck somewhere. This will ensure you do not spend too much time stranded at a particular step. \n",
    "- **We urge you to search for solutions on the internet too. That's what you'll do outdoors, and we think it is an essential part of learning to program.**\n",
    "- You can explore alternative ways to solve the problem.\n",
    "- Guided projects are not graded or reviewed. You need to code the solution and run it successfully to evaluate your progress.\n",
    "- We provide a model solution of the project against which you can compare your code for self-review.\n",
    "- The duration of this project is ONE week. You need to complete the project within that time.\n",
    "\n",
    "Let's begin!\n",
    "</div>"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "MgP30QK69pd2"
   },
   "source": [
    "# **Topic: Trading in the spot markets using future open interest**\n",
    "<div class=\"alert alert-info \">\n",
    "    <strong>Problem statement:</strong>\n",
    "\n",
    "In this project, you will perform the following using Python:\n",
    "- Handling spot data of the underlying asset\n",
    "- Handling futures OI data \n",
    "- Trading the underlying asset based on signals from the futures OI\n",
    "</div>\n",
    "\n",
    "See the below image for more clarity."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "OPLsu0c1TtxO"
   },
   "source": [
    "![idea.png](data:image/png;base64,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)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "jYcCaZT6o4_n"
   },
   "source": [
    "Reference:  https://www.shubhlaxmicommodity.com/2019/07/ncdex-price-volume-open-interest.html\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Model Solution\n",
    "In this notebook, we provide a model solution to the project's stock and futures strategy. You can refer to this if you are stuck in any step while building your solution. The features and parameters added here are not exhaustive or fine-tuned. \n",
    "\n",
    "The model solution guides you through answering problem statements posed in the project. The notebook structure is as follows:\n",
    "1. [Importing the libraries](#import)\n",
    "2. [Handling the spot data ](#preprocessing)\n",
    "3. [Running the  strategy and generating the trade book](#trades)\n",
    "4. [Analyzing the strategy using a trade book ](#analysis)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "In this guided project, we will trade instruments at the spot based on trend(indicated by spot prices) and confirm the momentum using the OI of the futures as indicated  in the First and Third Cases."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "zvQ52GvsDTba"
   },
   "source": [
    "<a id='import'></a>\n",
    "## Section 1: Importing the libraries"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "U4zolxCW_eig"
   },
   "source": [
    "- This will be the first step for any Python project that you do.\n",
    "- In this section, we import all required Python libraries used for computation."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "9breOeRfSDIH",
    "outputId": "9f7b00e0-1cf7-4b55-e806-f9d519ea24ad"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 1,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "6T96dBYfDQNe"
   },
   "source": [
    "<a id='preprocessing'></a>\n",
    "## Section 2: Handling the Spot Data"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "PCYeV61DTvs9",
    "outputId": "080ac046-53cd-4dff-9fab-248a552565fe"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 2,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Reading the data from CSV file\n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "hVGWpAXXYNh2",
    "outputId": "82ff474e-c61a-437f-d604-03791c604774"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 3,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Print the dataframe\n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "8wyKf-ACDIck"
   },
   "source": [
    "Now we need to extract the year and month for each data point. We will group later using the `df.groupby()` function because our future contracts have expiries, and we can't have any positions after that. So any trade initiated should be squared off before the expiration of the contract."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "5WNMwbKOFmuR",
    "outputId": "4382243e-9723-430e-cc7e-fb407c669794"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 4,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# We need to extract the year and month from the contract column. But the contract column we need to convert from int to string\n",
    "# Because the dataframe from the expiry of the futures contracts\n",
    "\n",
    "# Check the datatype for each column in the dataframe\n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "LJr-DoV8a1eT",
    "outputId": "33c84df8-d9ed-4888-884c-b840b18bcb12"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 5,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Convert contract column to string type\n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "RzshGu5yF2dj",
    "outputId": "5b3f5cde-e4c7-42e5-f139-27576e2ba115"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 6,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Check the datatype for each column in the dataframe\n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "CSgTjj4ckSOl",
    "outputId": "ee31685e-d62b-46c9-a02a-20fef83838d7"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 7,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Extract year and month of the expiry\n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "7zTDH-fja8Cg",
    "outputId": "6dd31b8c-341a-4e40-d33b-f548258b5086"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 8,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Print the dataframe\n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "0ESpHGHHC-aX"
   },
   "source": [
    "In this section, we can use various technical indicators like RSI, MA, Bollinger Band, MACD, etc. for generating the 'Trend' column in the data frame\n",
    "\n",
    "In this model solution, we would use  MA(5) crossover."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "E6pQZZGJDEda",
    "outputId": "2e65406b-de09-4971-b512-d80fb103e161"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 9,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Generate SMA(5) which is simple average of the last 5 days\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Today’s SMA line is below the close price line and the previous-day SMA line is above the previous-day close line\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Make a new column in dataframe and set it as 1 if there is bullish crossover else 0\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Today’s SMA line is above the close price line and the previous-day SMA line is below the previous-day close line\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# If there is bearish crossover make signal col -1  else let it be unchanged \n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "DvN2musSGuZj",
    "outputId": "e9102f75-0af5-4ff2-b9de-cd7eb0c56cf6"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 10,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Print the dataframe\n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "h_hHg0bRHfi1",
    "outputId": "b0d893f6-f11b-445f-b442-00eb75903819"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 11,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Print the number of trend signals\n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "thEa7Iz8DHJS"
   },
   "source": [
    "<a id='trade'></a>\n",
    "## Step 3: Running the strategy and generating the trade book"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "J4Zs8GFOTqu7"
   },
   "source": [
    "### Strategy details "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "VwUs-LFmDGZz"
   },
   "source": [
    "- We have 4 different months of expiry: 03/06/09/12. So the main idea is to group our data based on these expiries.\n",
    "- After grouping our data, for each group's initial 10 days we won't take any trade\n",
    "- After 10 days, we would daily monitor the OI data of the nearest future expiry.\n",
    "- Stock would be considered in momentum if today's OI is greater than the average of the last 10 days' OI.\n",
    "\n",
    "ENTRY\n",
    "\n",
    "- If the trend is bullish/bullish and there is sufficient momentum, we take the corresponding position in the spot  market\n",
    "\n",
    "EXIT\n",
    "\n",
    "- Target hit (If we achieve 5% profit)\n",
    "- Not Sufficient Momentum (If current day's OI is less than last 10 days' OI average)\n",
    "- Opposite Trend (If current trend is opposite of the previous trend)\n",
    "- Expiry (Square-off at the expiry day in case there is an  open position)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "9chqYp6PT2Vx"
   },
   "source": [
    "### Working of the below code"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "ysbT6ix0T4CS"
   },
   "source": [
    "We will loop over each of the dates in the data, take position whenever entry conditions are met, and square off positions (if any) when exit conditions are met, and update the completed trade in our trade book. \n",
    "\n",
    "We will backtest our strategy using the following steps:\n",
    "\n",
    "\n",
    "**Step-1**: Create an empty list from which we will store our completed trades and generate our tradebook. We also store the four different types of future expiry in our dataset.\n",
    "\n",
    "**Step-2**: We will group our data monthly and iterate through them individually. For each month, reset the count variable, store the last trading date for that month, and reset your position.\n",
    "\n",
    "**Step-3**: We will iterate through each row of the given month. For the initial 10 days, we don't take any trade and store the average Open Interest for the last 10 days.\n",
    "\n",
    "**Step-4**: After 10 days, if we don't have any position, we will check for entry signals. If any entry criteria is satisfied, we execute strategy and accordingly update our position. \n",
    "\n",
    "**Step-5**: If we have any existing positions, we will check for exit signals. If any exit criteria are satisfied, we execute strategy, square off our position, and reset our position.\n",
    "\n",
    "**Step-6**: After a trade  is squared off, we store  all the corresponding details of the entire trade as a dictionary in the original list. \n",
    "\n",
    "**Step-7**: After we process all the data, we have a list of all completed trades as a dictionary. We convert this list into dataframe and generate our tradebook. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "piomUdImT2tv"
   },
   "source": [
    "### Strategy code"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "LtRUzQNv2eCS",
    "outputId": "a0f65ed4-350f-42d1-893b-8ee97c62246a"
   },
   "outputs": [],
   "source": [
    "# Make a list of dictionaries which will be latter converted in a tradebook dataframe\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Four types of expiries\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Map each diary to a number\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Set the last expiry\n",
    "# Last will be used to check next contract is valid\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# If next contract is not in order so we won't  trade this\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Initial day for new group  \n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Average of last 10 days OI\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# New trade will be stored in a dictionary\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Iterate through each row of the current month \n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Check if 10 days have passed for the new group\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Average of last 10 days OI\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# LONG TRADE ENTRY \n",
    "\n",
    "# If bullish trend and sufficient momentum\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Update postion\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Enter new trade log\n",
    "\n",
    "# Store date of entry\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Store entry position\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Store entry price\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Store quantity transacted\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# SHORT TRADE ENTRY \n",
    "\n",
    "# If bearish trend and sufficient momentum\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Update position\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Enter a new trade log\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "## ************************************************************************************************ ##\n",
    "\n",
    "# LONG TRADE SQUARE OFF SIGNAL DUE TO OPP TREND\n",
    "\n",
    "# Trend Reverse\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Save complete trade log\n",
    "\n",
    "# Store date of exit\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Store price at time of exit\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Calculate profit\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Store reason for exit\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Store trade\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Set default values\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "# Take fresh position in reversed trend\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Enter a new trade log\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Check OI momentum declining\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Save complete trade log\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "\n",
    "# Check if the 5% take-profit target is hit\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Save complete trade log\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Square-off at the expiry day in case there is an  open position\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Save complete trade log\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Set default values\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "## ************************************************************************************** **\n",
    "\n",
    "\n",
    "\n",
    "# SHORT TRADE SQUARE OFF SIGNAL OPP TREND\n",
    "\n",
    "# Trend Reverse\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Save complete trade log\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Take fresh position in reversed trend\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Enter new trade log\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "\n",
    "# Check OI momentum declining\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Save the complete trade log\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Check if the 5% take-profit target is hit\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Save complete trade log\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Square-off at the expiry day in case there is an  open position \n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Save complete trade log\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Increment cnt to go to next row of the sliced dateframe\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Get net month whose expiry is available\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Make a trade book of all the appended completed trades\n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "LtRUzQNv2eCS",
    "outputId": "a0f65ed4-350f-42d1-893b-8ee97c62246a"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 12,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Print the tradeboook\n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "buSzCCBJCrrr"
   },
   "source": [
    "<a id='analysis'></a>\n",
    "## Step 4: Analyzing the Strategy using Tradebook"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "F4Oq4AcAAuZ8"
   },
   "source": [
    "We will compute key metrics to evaluate our strategy\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "UnRnalxICxnW",
    "outputId": "4de25a0a-7159-47f6-e9af-69875981bad1"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 13,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Get the trades with profit > 0, and by applying len function, we get the  number of winning trades\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Get the trades with profit < 0, and by applying len function, we get the number of losing trades\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Get the number of all trades\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Number of wins trades/no of total trades\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Number of loss trades/no of total trades\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Find all the profitable trades and adding their profit\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Total profit / Number of winning trades\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Find all the losing trades and adding their losses\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Total loss/Number of losing trades\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Average profit/Average loss\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Win ratio * Average profit/Loss ratio * Average loss\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Store the important metrics in a list\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Convert list into dataframe\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Print the dataframe\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 36
    },
    "id": "d1qXV0k6HzEU",
    "outputId": "971b614d-3f2d-4b09-f299-d4ca51ed5a3d"
   },
   "outputs": [
    {
     "data": {
      "application/vnd.google.colaboratory.intrinsic+json": {
       "type": "string"
      },
      "text/plain": [
       "'\\nAdd your code here\\n'"
      ]
     },
     "execution_count": 15,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Generate a column for cumulative profit\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Define the figure size for the plot\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Plot the close price of the underlying\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Set the title and axis labels\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Add a legend to the axis\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Define the tick size for the x-axis and y-axis\n",
    "'''\n",
    "Add your code here\n",
    "'''\n",
    "\n",
    "# Show the plot\n",
    "'''\n",
    "Add your code here\n",
    "'''"
   ]
  }
 ],
 "metadata": {
  "colab": {
   "provenance": []
  },
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.13"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 1
}
